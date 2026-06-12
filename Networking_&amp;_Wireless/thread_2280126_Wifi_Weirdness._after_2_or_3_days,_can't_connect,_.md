---
title: "Wifi Weirdness. after 2 or 3 days, can't connect, can't see APs."
date: 2015-05-28
forum: Networking &amp; Wireless
---

### Post by xoagray on 2015-05-28
I have a Dell XPS ONE 23" With a Broadcom 4321 Wifi chipset running Ubuntu 14.04 and everything is smooth sailing except for my Wifi.  It appears to work fine at first, sees AP's and can connect without issue.  Transferring files and browsing works fine.  I even use the computer as a router.  All's well... for 2 or 3 days.  After that, strange things happen.  Sometimes I'll notice the signal status icon in the system tray is reading 0 signal, but I'm still connected.  Other times it'll just disconnect. And when I click on it to choose an AP to reconnect, it doesn't show any available. (I can still see available ones via my phone, other computers, etc) Sometimes (rarely) disabling and enabling the Wifi will bring the AP's back and it will reconnect.  More often disabling and enabling does nothing.  When the computer was running Windows, the Wifi behaved just fine, but I'm loathe to reinstall Windows on this thing when it's otherwise doing so much better under Ubuntu.  

I've tried purging and reinstalling the related wifi module (B43) to no avail, and so far this issue has stumped the crowd at #Ubuntu. I've seen it work, I've seen it not work.  But this is the first time I've seen it work great, transfer speeds are great, etc, then just decide randomly not to.  Any ideas would be appreciated.  

Thanks,

Edit: 

Getting some errors in dmesg this time. 

[13433.006706] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:e0:4c:81:86:d1   profile =00:02:6f:bd:4f:c3
[13433.006734] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:e0:4c:81:86:d1   profile =00:02:6f:bd:4f:c3
[13439.006887] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:e0:4c:81:86:d1   profile =00:02:6f:bd:4f:c3
[13439.006934] ERROR @wl_cfg80211_get_station : Wrong Mac address, mac = 00:e0:4c:81:86:d1   profile =00:02:6f:bd:4f:c3
[13444.575244] cfg80211: Calling CRDA to update world regulatory domain
[13444.951190] cfg80211: World regulatory domain updated:
[13444.951197] cfg80211:  DFS Master region: unset
[13444.951200] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[13444.951205] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[13444.951209] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[13444.951213] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[13444.951216] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[13444.951220] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[20165.345327] cfg80211: Calling CRDA to update world regulatory domain
[20165.364002] cfg80211: World regulatory domain updated:
[20165.364052] cfg80211:  DFS Master region: unset
[20165.364055] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[20165.364058] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[20165.364061] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[20165.364064] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[20165.364066] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[20165.364069] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[20206.866315] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[20207.866895] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[20230.042382] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)

Long stream of those MAC address errors then what you see below them.

---

### Post by NoWayWin8 on 2015-05-28
Did someone change your network settings for the WifI adapter? A neighbor might be using the same SSID on his WiFi...do you have it locked to your WiFi AP's Mac?

---

### Post by xoagray on 2015-06-12
Sorry for taking so long to reply to this.  For some reason I couldn't log into the forums again till today.  But no, no one has changed my settings.  Also the other WiFi devices I own are still able to see the WiFi on their own with no issue. It's just the Ubuntu machine having the problem.  And no, I don't have the WiFI on the Ubuntu machine locked to any one Mac address.  Basically over time it just stops seeing other wifi AP's, and won't even reconnect if I tell it specifically the details and tell it to connect to a hidden network.  I've looked around a bit in the last two weeks and it appears this might be a bug that has been active between Ubuntu and the Broadcom STA driver since the 12.04 days and still isn't fixed.
I should also note that sometimes the up time for my WiFi has been much shorter.  Just a few hours at times lately, and the only thing I can do to get it to work again is a full on reboot.  Even disabling and enabling the wifi (or networking all together) won't bring it back.

---

