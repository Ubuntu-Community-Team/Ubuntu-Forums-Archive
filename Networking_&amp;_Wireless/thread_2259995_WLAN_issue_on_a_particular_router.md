---
title: "WLAN issue on a particular router"
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by luis45 on 2015-01-08
Hello,

I'm having issues with my WLAN connection, sometimes it works fine, others besides it saying i'm connected i can't really reach anything on the network. 

I've worked around this using tethering with my phone to the same network and it works fine. Here's a syslog output that might help:

```
Jan  8 15:24:31 biscoito wpa_supplicant[1168]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jan  8 15:24:31 biscoito NetworkManager[5354]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  8 15:24:32 biscoito wpa_supplicant[1168]: wlan0: SME: Trying to authenticate with 88:03:55:0d:10:2c (SSID='Mirzo' freq=2457 MHz)
Jan  8 15:24:32 biscoito kernel: [53251.008965] wlan0: authenticate with 88:03:55:0d:10:2c
Jan  8 15:24:32 biscoito NetworkManager[5354]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  8 15:24:32 biscoito kernel: [53251.030874] wlan0: send auth to 88:03:55:0d:10:2c (try 1/3)
Jan  8 15:24:32 biscoito wpa_supplicant[1168]: wlan0: Trying to associate with 88:03:55:0d:10:2c (SSID='Mirzo' freq=2457 MHz)
Jan  8 15:24:32 biscoito kernel: [53251.033603] wlan0: authenticated
Jan  8 15:24:32 biscoito kernel: [53251.036258] wlan0: associate with 88:03:55:0d:10:2c (try 1/3)
Jan  8 15:24:32 biscoito NetworkManager[5354]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan  8 15:24:32 biscoito wpa_supplicant[1168]: wlan0: Associated with 88:03:55:0d:10:2c
Jan  8 15:24:32 biscoito kernel: [53251.064396] wlan0: RX AssocResp from 88:03:55:0d:10:2c (capab=0x411 status=0 aid=4)
Jan  8 15:24:32 biscoito kernel: [53251.064492] wlan0: associated
Jan  8 15:24:32 biscoito kernel: [53251.064649] cfg80211: Calling CRDA for country: DE
Jan  8 15:24:32 biscoito NetworkManager[5354]: <info> (wlan0): supplicant interface state: associating -> associated
Jan  8 15:24:32 biscoito kernel: [53251.069647] ath: EEPROM regdomain: 0x8114
Jan  8 15:24:32 biscoito kernel: [53251.069655] ath: EEPROM indicates we should expect a country code
Jan  8 15:24:32 biscoito kernel: [53251.069659] ath: doing EEPROM country->regdmn map search
Jan  8 15:24:32 biscoito kernel: [53251.069663] ath: country maps to regdmn code: 0x37
Jan  8 15:24:32 biscoito kernel: [53251.069666] ath: Country alpha2 being used: DE
Jan  8 15:24:32 biscoito kernel: [53251.069669] ath: Regpair used: 0x37
Jan  8 15:24:32 biscoito kernel: [53251.069674] ath: regdomain 0x8114 dynamically updated by country IE
Jan  8 15:24:32 biscoito kernel: [53251.069715] cfg80211: Regulatory domain changed to country: DE
Jan  8 15:24:32 biscoito kernel: [53251.069719] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  8 15:24:32 biscoito kernel: [53251.069724] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jan  8 15:24:32 biscoito kernel: [53251.069729] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jan  8 15:24:32 biscoito kernel: [53251.069733] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Jan  8 15:24:32 biscoito kernel: [53251.069737] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
Jan  8 15:24:32 biscoito kernel: [53251.069741] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Jan  8 15:24:32 biscoito wpa_supplicant[1168]: wlan0: WPA: Key negotiation completed with 88:03:55:0d:10:2c [PTK=CCMP GTK=CCMP]
Jan  8 15:24:32 biscoito wpa_supplicant[1168]: wlan0: CTRL-EVENT-CONNECTED - Connection to 88:03:55:0d:10:2c completed [id=0 id_str=]
Jan  8 15:24:32 biscoito NetworkManager[5354]: <info> (wlan0): supplicant interface state: associated -> completed
Jan  8 15:24:59 biscoito kernel: [53277.568094] wlan0: deauthenticated from 88:03:55:0d:10:2c (Reason: 3)
Jan  8 15:24:59 biscoito wpa_supplicant[1168]: wlan0: CTRL-EVENT-DISCONNECTED bssid=88:03:55:0d:10:2c reason=3
Jan  8 15:24:59 biscoito NetworkManager[5354]: <warn> Connection disconnected (reason 3)
Jan  8 15:24:59 biscoito kernel: [53277.595050] cfg80211: Calling CRDA to update world regulatory domain
Jan  8 15:24:59 biscoito NetworkManager[5354]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jan  8 15:24:59 biscoito kernel: [53277.603430] cfg80211: World regulatory domain updated:
Jan  8 15:24:59 biscoito kernel: [53277.603450] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  8 15:24:59 biscoito kernel: [53277.603458] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 15:24:59 biscoito kernel: [53277.603465] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 15:24:59 biscoito kernel: [53277.603471] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  8 15:24:59 biscoito kernel: [53277.603475] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 15:24:59 biscoito kernel: [53277.603479] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

...and this repeats all over the place...

```

I've already tried to disable IPv6 and N mode (altough not sure if I did it right) and didn't help at all.

Hope you can help me fixing this, thanks :)

---

