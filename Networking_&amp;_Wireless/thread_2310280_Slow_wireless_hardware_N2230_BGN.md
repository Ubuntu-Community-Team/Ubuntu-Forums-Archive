---
title: "Slow wireless hardware N2230 BGN"
date: 2016-01-17
forum: Networking &amp; Wireless
---

### Post by carl4926 on 2016-01-17
For some strange reason this device is performing poorly
```
04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
	Kernel driver in use: iwlwifi



```

dmesg has this, but I guess it's just blurb
```
[ 9897.685382] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled[ 9897.693012] iwlwifi 0000:04:00.0: Radio type=0x2-0x0-0x0
[ 9897.750826] PM: resume of devices complete after 979.939 msecs
[ 9897.751252] PM: Finishing wakeup.
[ 9897.751253] Restarting tasks ... done.
[ 9897.763912] cfg80211: World regulatory domain updated:
[ 9897.763916] cfg80211:  DFS Master region: unset
[ 9897.763917] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 9897.763919] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 9897.763921] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 9897.763922] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 9897.763924] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 9897.763925] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 9898.451134] wlan0: authenticate with 00:37:b
[ 9898.452860] wlan0: send auth to 00:37: (try 1/3)
[ 9898.456363] wlan0: authenticated
[ 9898.459362] wlan0: associate with 00:37 (try 1/3)
[ 9898.463064] wlan0: RX AssocResp from 00:37 (capab=0x411 status=0 aid=2)
[ 9898.465688] wlan0: associated
[ 9898.465779] cfg80211: Calling CRDA for country: GB
[ 9898.468868] cfg80211: Regulatory domain changed to country: GB
[ 9898.468874] cfg80211:  DFS Master region: unset
[ 9898.468877] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 9898.468882] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 9898.468885] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[ 9898.468888] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
[ 9898.468891] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
[ 9898.468895] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)



```

FYI it's the same performance in Windows

---

