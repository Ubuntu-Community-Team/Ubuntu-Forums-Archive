---
title: "Dropping wifi Ubuntu 14.04: Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by Joost_Plas on 2015-07-16
Hi guys,


I'm having some annoying wifi problems.
I run a pretty minimal Ubuntu 14.04.2 server installation with LXDE (mostly based on this guide: [http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/](http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/))


I run this on a Gigabyte Brix GB-BXCEH-3205.


I'm having some annoying wifi connection problems. I've tried this both with the internal wifi adapter and with a external one: TL-WN722N.
The problem is that regularly I cannot connect from other machines to the Brix anymore. I try this with SSH. Usually when I leave the machine alone for a few hours and try to connect I have no access through SSH and I also don't see the machine when I do a scan of my network. When I enter the terminal on the Brix and try 'ping [www.google.nl]("http://www.google.nl")' it always works. After that I can also again connect from the outside to the machine again. 


I get a lot of 'deauthenticated' messages in my syslog. Seems related, but so far I could not prove the relation 100% by looking at the times. 


I tried to add a lot of debug info. This is all with a working internet connection at the moment, but problems earlier this day (around 14.42 in log).
Any help would be much appreciated. It is crippling my setup.


/var/log/syslog
```

Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.262119] wlan0: deauthenticated from 50:60:28:2a:34:83 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.311620] cfg80211: Calling CRDA to update world regulatory domain
Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.314366] cfg80211: World regulatory domain updated:
Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.314371] cfg80211:  DFS Master region: unset
Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.314372] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.314376] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.314378] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.314380] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.314382] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:16:27 pandora-client-1 kernel: [ 3842.314384] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.799855] wlan0: authenticate with 50:60:28:29:b3:13
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.803012] wlan0: send auth to 50:60:28:29:b3:13 (try 1/3)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.809709] wlan0: authenticated
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.810111] wlan0: associate with 50:60:28:29:b3:13 (try 1/3)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.814802] wlan0: RX AssocResp from 50:60:28:29:b3:13 (capab=0x1011 status=0 aid=5)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.816550] wlan0: associated
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.816636] cfg80211: Calling CRDA for country: NL
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.821391] cfg80211: Regulatory domain changed to country: NL
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.821395] cfg80211:  DFS Master region: unset
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.821397] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.821400] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.821402] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.821404] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.821406] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.821408] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jul 16 13:16:30 pandora-client-1 kernel: [ 3845.896812] wlan0: Limiting TX power to 19 (30 - 11) dBm as advertised by 50:60:28:29:b3:13
Jul 16 13:17:01 pandora-client-1 CRON[1853]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.922679] wlan0: deauthenticated from 50:60:28:29:b3:13 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.962118] cfg80211: Calling CRDA to update world regulatory domain
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.964864] cfg80211: World regulatory domain updated:
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.964869] cfg80211:  DFS Master region: unset
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.964870] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.964874] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.964876] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.964878] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.964880] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:48:37 pandora-client-1 kernel: [ 5771.964882] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.199126] wlan0: authenticate with 50:60:28:2a:34:93
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.202162] wlan0: send auth to 50:60:28:2a:34:93 (try 1/3)
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.203839] wlan0: authenticated
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.204696] wlan0: associate with 50:60:28:2a:34:93 (try 1/3)
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.208795] wlan0: RX AssocResp from 50:60:28:2a:34:93 (capab=0x1011 status=0 aid=6)
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.210255] wlan0: associated
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.210313] cfg80211: Calling CRDA for country: NL
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.215083] wlan0: Limiting TX power to 19 (30 - 11) dBm as advertised by 50:60:28:2a:34:93
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.215112] cfg80211: Regulatory domain changed to country: NL
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.215114] cfg80211:  DFS Master region: unset
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.215116] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.215119] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.215121] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.215123] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.215125] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jul 16 13:48:40 pandora-client-1 kernel: [ 5775.215127] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jul 16 14:17:01 pandora-client-1 CRON[2042]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.601113] wlan0: deauthenticated from 50:60:28:2a:34:93 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.661884] cfg80211: Calling CRDA to update world regulatory domain
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.666999] cfg80211: World regulatory domain updated:
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.667005] cfg80211:  DFS Master region: unset
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.667006] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.667010] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.667012] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.667014] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.667016] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:18:53 pandora-client-1 kernel: [ 7587.667018] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.946019] wlan0: authenticate with 50:60:28:2a:34:83
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.949394] wlan0: send auth to 50:60:28:2a:34:83 (try 1/3)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.952254] wlan0: authenticated
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.956358] wlan0: associate with 50:60:28:2a:34:83 (try 1/3)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.972445] wlan0: RX AssocResp from 50:60:28:2a:34:83 (capab=0x1431 status=0 aid=1)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.976508] wlan0: associated
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.976574] cfg80211: Calling CRDA for country: NL
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.979355] cfg80211: Regulatory domain changed to country: NL
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.979360] cfg80211:  DFS Master region: unset
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.979362] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.979365] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.979367] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.979369] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.979371] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7590.979373] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jul 16 14:18:57 pandora-client-1 kernel: [ 7591.073082] wlan0: Limiting TX power to 5 (20 - 15) dBm as advertised by 50:60:28:2a:34:83
Jul 16 14:44:53 pandora-client-1 kernel: [ 9146.869946] usb 1-4: new low-speed USB device number 3 using xhci_hcd
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.073489] usb 1-4: New USB device found, idVendor=04d9, idProduct=1603
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.073495] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.073498] usb 1-4: Product: USB Keyboard
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.073500] usb 1-4: Manufacturer:  
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.073660] usb 1-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.073668] usb 1-4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.109569] usbcore: registered new interface driver usbhid
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.109573] usbhid: USB HID core driver
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.112511] input:   USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:04D9:1603.0001/input/input9
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.166216] hid-generic 0003:04D9:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:14.0-4/input0
Jul 16 14:44:53 pandora-client-1 kernel: [ 9147.168609] input:   USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.1/0003:04D9:1603.0002/input/input10
Jul 16 14:44:54 pandora-client-1 kernel: [ 9147.222177] hid-generic 0003:04D9:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:14.0-4/input1
Jul 16 14:44:55 pandora-client-1 kernel: [ 9148.777242] usb 1-3: new low-speed USB device number 4 using xhci_hcd
Jul 16 14:44:55 pandora-client-1 kernel: [ 9148.908419] usb 1-3: New USB device found, idVendor=046d, idProduct=c05a
Jul 16 14:44:55 pandora-client-1 kernel: [ 9148.908427] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jul 16 14:44:55 pandora-client-1 kernel: [ 9148.908430] usb 1-3: Product: USB Optical Mouse
Jul 16 14:44:55 pandora-client-1 kernel: [ 9148.908432] usb 1-3: Manufacturer: Logitech
Jul 16 14:44:55 pandora-client-1 kernel: [ 9148.908673] usb 1-3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jul 16 14:44:55 pandora-client-1 kernel: [ 9148.910902] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:046D:C05A.0003/input/input11
Jul 16 14:44:55 pandora-client-1 kernel: [ 9148.965391] hid-generic 0003:046D:C05A.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:14.0-3/input0
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.591530] wlan0: deauthenticated from 50:60:28:2a:34:83 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.701443] cfg80211: Calling CRDA to update world regulatory domain
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.704724] cfg80211: World regulatory domain updated:
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.704729] cfg80211:  DFS Master region: unset
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.704731] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.704734] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.704737] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.704739] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.704741] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:45:28 pandora-client-1 kernel: [ 9181.704742] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.002318] wlan0: authenticate with 50:60:28:29:b3:13
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.005709] wlan0: send auth to 50:60:28:29:b3:13 (try 1/3)
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.007127] wlan0: authenticated
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.008146] wlan0: associate with 50:60:28:29:b3:13 (try 1/3)
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.012786] wlan0: RX AssocResp from 50:60:28:29:b3:13 (capab=0x1011 status=0 aid=3)
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.015275] wlan0: associated
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.015330] cfg80211: Calling CRDA for country: NL
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.018073] cfg80211: Regulatory domain changed to country: NL
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.018078] cfg80211:  DFS Master region: unset
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.018079] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.018083] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.018085] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.018087] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.018089] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
Jul 16 14:45:31 pandora-client-1 kernel: [ 9185.018091] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jul 16 14:45:32 pandora-client-1 kernel: [ 9185.380327] wlan0: Limiting TX power to 19 (30 - 11) dBm as advertised by 50:60:28:29:b3:13
 
```


uname -a
```
Linux pandora-client-1 4.1.1-040101-generic #201507030635 SMP Fri Jul 3 10:38:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```


lspci -nnk | grep -iA2 net
```
02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
    Kernel driver in use: iwlwifi
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
```


lsusb
```
Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 005: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 006: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


ifconfig -a
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


p3p1      Link encap:Ethernet  HWaddr fc:aa:14:eb:d9:cc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr f4:06:69:17:5d:45  
          inet addr:10.100.0.45  Bcast:10.100.255.255  Mask:255.255.0.0
          inet6 addr: fe80::f606:69ff:fe17:5d45/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65963 errors:0 dropped:2 overruns:0 frame:0
          TX packets:21020 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88296881 (88.2 MB)  TX bytes:2617808 (2.6 MB)
```


route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.100.0.1      0.0.0.0         UG    0      0        0 wlan0
10.100.0.0      0.0.0.0         255.255.0.0     U     0      0        0 wlan0
```


iwconfig
```
wlan0     IEEE 802.11abgn  ESSID:"DHS_Offices"  
          Mode:Managed  Frequency:5.5 GHz  Access Point: 50:60:28:29:B3:13   
          Bit Rate=6 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:5   Missed beacon:0


p3p1      no wireless extensions.


lo        no wireless extensions.
```


lsmod
```
Module                  Size  Used by
hid_generic            16384  0 
usbhid                 53248  0 
ctr                    16384  2 
ccm                    20480  2 
arc4                   16384  2 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       16384  0 
coretemp               16384  0 
kvm_intel             155648  0 
kvm                   491520  1 kvm_intel
iwlmvm                294912  0 
mac80211              745472  1 iwlmvm
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
cryptd                 20480  1 ghash_clmulni_intel
btusb                  49152  0 
iwlwifi               200704  1 iwlmvm
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             516096  4 btbcm,btusb,btintel
cfg80211              552960  3 iwlwifi,mac80211,iwlmvm
snd_hda_codec_hdmi     53248  1 
lpc_ich                24576  0 
snd_soc_rt5640         94208  0 
snd_hda_codec_realtek    90112  1 
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_hda_intel          32768  1 
i915                 1097728  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hda_core           32768  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_controller
snd_hwdep              16384  1 snd_hda_codec
snd_soc_core          196608  1 snd_soc_rt5640
snd_compress           20480  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
video                  20480  1 i915
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
dw_dmac                16384  0 
drm_kms_helper        126976  1 i915
snd_timer              32768  2 snd_pcm,snd_seq
dw_dmac_core           28672  1 dw_dmac
snd_soc_sst_acpi       16384  0 
drm                   352256  6 i915,drm_kms_helper
i2c_hid                20480  0 
hid                   114688  3 i2c_hid,hid_generic,usbhid
mei_me                 24576  0 
snd                    86016  14 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
8250_dw                16384  0 
i2c_designware_platform    16384  0 
mei                    90112  1 mei_me
i2c_designware_core    16384  1 i2c_designware_platform
spi_pxa2xx_platform    24576  0 
shpchp                 40960  0 
tpm_crb                16384  0 
soundcore              16384  1 snd
acpi_pad               20480  0 
mac_hid                16384  0 
i2c_algo_bit           16384  1 i915
lp                     20480  0 
nls_iso8859_1          16384  1 
parport                45056  1 lp
sdhci_acpi             16384  0 
sdhci                  45056  1 sdhci_acpi
r8169                  81920  0 
mii                    16384  1 r8169
ahci                   36864  3 
libahci                32768  1 ahci


iwlist -scan
[CODE]wlan0     Scan completed :
          Cell 01 - Address: 50:60:28:29:B3:13
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"DHS_Offices"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000099025300dda
                    Extra: Last beacon: 1153368ms ago
                    IE: Unknown: 000B4448535F4F666669636573
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030164
                    IE: Unknown: 070A4E4C20240817640B1E00
                    IE: Unknown: 20010B
                    IE: Unknown: 23021300
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3302510B
                    IE: Unknown: 46050200010000
                    IE: Unknown: 2D1A6C001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1664080800000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101820003A5000027A5000042435E0062432F00
                    IE: Unknown: DD1E00904C336C001BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3464080800000000000000000000000000000000000000
                    IE: Unknown: DD42000F7DF950602829B300BF81E826585200130000000000000000000001FC00000000000000000000000000000000000000000000000000000000000000000000FA44


p3p1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.
```




[/CODE]


/etc/network/interfaces
```
auto wlan0
iface wlan0 inet static
pre-up wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -B
post-down killall -q wpa_supplicant
address 10.100.0.45
gateway 10.100.0.1
netmask 255.255.0.0
dns-nameservers 8.8.8.8 8.8.4.4
```


/etc/wpa_supplicant.conf
```



network={
        ssid="DHS_Offices"
        scan_ssid=1
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=CCMP
        #psk="t03ts3nb0rd"
        psk=bb699f3efe3cc51f29a40b2371c2635d1283a4af98a6b50f856db28bde45d20f
}
```

---

### Post by Joost_Plas on 2015-07-17
Sorry forgot to post wireless-info.
This is run after a fresh boot (where wireless works).

```


########## wireless info START ##########


Report from: 17 Jul 2015 09:00 CEST +0200


Booted last: 17 Jul 2015 08:59 CEST +0200


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 4.1.1-040101-generic #201507030635 SMP Fri Jul 3 10:38:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


sed: can't read /home/pandora/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
	Kernel driver in use: iwlwifi


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


'pccardctl' is not installed (package "pcmciautils").


##### rfkill ############################


./wireless-info: line 191: rfkill: command not found


##### lsmod #############################


snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
iwlmvm                294912  0 
mac80211              745472  1 iwlmvm
iwlwifi               200704  1 iwlmvm
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
cfg80211              552960  3 iwlwifi,mac80211,iwlmvm


##### interfaces ########################


auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet static
pre-up wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -B
post-down killall -q wpa_supplicant
address 10.100.0.45
gateway 10.100.0.1
netmask 255.255.0.0
dns-nameservers 8.8.8.8 8.8.4.4


##### ifconfig ##########################


p3p1      Link encap:Ethernet  HWaddr <MAC 'p3p1' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.100.0.45  Bcast:10.100.255.255  Mask:255.255.0.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:254732 (254.7 KB)  TX bytes:45219 (45.2 KB)


##### iwconfig ##########################


p3p1      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"DHS_Offices"  
          Mode:Managed  Frequency:5.7 GHz  Access Point: <MAC 'DHS_Offices' [AC7]>   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.100.0.1      0.0.0.0         UG    0      0        0 wlan0
10.100.0.0      0.0.0.0         255.255.0.0     U     0      0        0 wlan0


##### resolv.conf #######################


nameserver 8.8.8.8
nameserver 8.8.4.4


##### network managers ##################


Installed:


	None found.


Running:


	None found.


##### NetworkManager info ###############


NetworkManager is not installed (package "network-manager").


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


##### NetworkManager.conf ###############


grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory


##### NetworkManager profiles ###########


No NetworkManager profiles found.


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


p3p1      no frequency information.


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:5.7 GHz (Channel 140)


##### iwlist scan #######################


p3p1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)
      1   APs on   Frequency:5.24 GHz (Channel 48)
      3   APs on   Frequency:5.7 GHz (Channel 140)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Pandora Test' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"Pandora Test"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006b3cb8e2
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DHS_Offices' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"DHS_Offices"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006e8d03f8111
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'DHS_Guests' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"DHS_Guests"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006e8d03f758d
                    Extra: Last beacon: 84ms ago
          Cell 04 - Address: <MAC 'DHS_Engineering' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"DHS_Engineering"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006e8d03f48bf
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'VideobriX50' [AC5]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"VideobriX50"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002bbb83eea06
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'DHS_Engineering' [AC6]>
                    Channel:140
                    Frequency:5.7 GHz (Channel 140)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"DHS_Engineering"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006e8cf4b29de
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'DHS_Offices' [AC7]>
                    Channel:140
                    Frequency:5.7 GHz (Channel 140)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"DHS_Offices"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006e8cf4b2e56
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'DHS_Guests' [AC8]>
                    Channel:140
                    Frequency:5.7 GHz (Channel 140)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"DHS_Guests"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006e8cf4b2c2d
                    Extra: Last beacon: 84ms ago
          Cell 09 - Address: <MAC 'DHS_Guests' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"DHS_Guests"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000099f6e4a2eb4
                    Extra: Last beacon: 84ms ago
          Cell 10 - Address: <MAC 'VideobriX24' [AC10]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"VideobriX24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002bbb8a0218f
                    Extra: Last beacon: 2928ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.1.1-040101-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     4BAA00B1F9481F9B825BC4D
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.1.1-040101-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        42:74:6F:18:A0:6E:DB:F6:36:F0:99:72:79:E2:3C:8A:BF:10:BA:E7
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.1.1-040101-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5F217E3E605BFE2A9C4566D
depends:        cfg80211
intree:         Y
vermagic:       4.1.1-040101-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        42:74:6F:18:A0:6E:DB:F6:36:F0:99:72:79:E2:3C:8A:BF:10:BA:E7
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.1.1-040101-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-IWL3160_UCODE_API_OK.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     B72437DD648288F0DE2EB8E
depends:        cfg80211
intree:         Y
vermagic:       4.1.1-040101-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        42:74:6F:18:A0:6E:DB:F6:36:F0:99:72:79:E2:3C:8A:BF:10:BA:E7
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/4.1.1-040101-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     2151DA0D0F0543B97999E87
depends:        
intree:         Y
vermagic:       4.1.1-040101-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        42:74:6F:18:A0:6E:DB:F6:36:F0:99:72:79:E2:3C:8A:BF:10:BA:E7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


chown -R pandora /dev/dri
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x08b3 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


##### dmesg #############################


[    3.284780] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    3.287209] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3160-13.ucode failed with error -2
[    3.287977] iwlwifi 0000:02:00.0: Unsupported splx structure
[    3.290735] iwlwifi 0000:02:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[    3.357739] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
[    3.361705] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    3.361964] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[    3.462460] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    3.538979] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.848117] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled (repeated 4 times)
[    3.970733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.251874] wlan0: authenticate with <MAC 'DHS_Offices' [AC7]>
[    7.255689] wlan0: send auth to <MAC 'DHS_Offices' [AC7]> (try 1/3)
[    7.257223] wlan0: authenticated
[    7.261138] wlan0: associate with <MAC 'DHS_Offices' [AC7]> (try 1/3)
[    7.265476] wlan0: RX AssocResp from <MAC 'DHS_Offices' [AC7]> (capab=0x1011 status=0 aid=3)
[    7.269344] wlan0: associated
[    7.269379] wlan0: Limiting TX power to 19 (30 - 11) dBm as advertised by <MAC 'DHS_Offices' [AC7]>
[    7.269395] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by clayton-nog on 2015-07-17
the same problem here, look:

```

kernel: [41408.816688] wlan0: deauthenticated from 98:fc:11:d4:0b:44 (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
kernel: [41264.680505] wlan0: deauthenticating from 98:fc:11:d4:0b:44 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)

```

---

### Post by Joost_Plas on 2015-07-24
It seems to be a suspend / idle issue.
When I leave my system idle (no suspend, power management is disabled) for a while I cannot connect from the outside anymore.
I can 'fix' this by just plugging in a keyboard and mouse on the remote machine and open a terminal. After that the connection from outside works again. I don't even have to activate the network or ping something, it just works.

Any tips how to prevent this?

---

### Post by brennanhm on 2015-09-21
I know this thread is several months old now, but I may have a solution that others will find useful. I was having the same problem with intermittent wireless disconnects and seeing "Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA" in the syslog. What I ended up doing was disabling power management for the wireless adapter. Afterwards, the disconnects stopped. I'm running Linux Mint 17.2 with an Intel Wireless 3160 adapter.

To check if power management is enabled just issue: [B]iwconfig
[/B]Look for the output: *Power Management: on*
The command to disable power management is: **sudo iwconfig wlan0 power off**  

You can create a script in /etc/pm/power.d/ that will disable power management upon boot. Add the following to your favorite text editor and save it as "wireless" in /etc/pm/power.d/wireless

```

#!/bin/sh
iwconfig wlan0 power off
  
```

Finally, make it executable:  **sudo chmod +x /etc/pm/power.d/wireless**
Hope that helps someone.

---

