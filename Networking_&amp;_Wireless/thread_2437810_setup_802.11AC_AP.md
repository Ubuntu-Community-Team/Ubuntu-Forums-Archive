---
title: "setup 802.11AC AP"
date: 2020-02-29
forum: Networking &amp; Wireless
---

### Post by bjlockie on 2020-02-29
I'm trying to set up a 802.11AC AP and I can't seem to get the channel I want.
I can do an IEEE 802.11an (n on 5GHz?) on channel 48 (frequency=5240).
$ iwconfig
wlan0  IEEE 802.11an  ESSID:"local50"  Nickname:"<WIFI@REALTEK>"
          Mode:Master  Frequency:5.24 GHz  Access Point: xx
          Bit Rate:144.4 Mb/s

I looked at the chart at [https://en.wikipedia.org/wiki/List_of_WLAN_channels#5.0_GHz_(802.11j)_WLAN](https://en.wikipedia.org/wiki/List_of_WLAN_channels#5.0_GHz_(802.11j)_WLAN) 
and chose channel 42 (frequency 5210).
I want to avoid the NO_IR and RADAR channels.

This is from wpa_supplicant -d:

1. nl80211: Regulatory information - country=CA (DFS-FCC)
nl80211: 2402-2472 @ 40 MHz 30 mBm
nl80211: 5150-5250 @ 80 MHz 23 mBm (no outdoor)
nl80211: 5250-5350 @ 80 MHz 24 mBm (DFS)
nl80211: 5470-5600 @ 80 MHz 24 mBm (DFS)
nl80211: 5650-5730 @ 80 MHz 24 mBm (DFS)
nl80211: 5735-5835 @ 80 MHz 30 mBm
nl80211: Added 802.11b mode based on 802.11g information

Is this information from the country_code I configured?

2. nl80211: Mode IEEE 802.11g: 2412 2417 2422 2427 2432 2437 2442 2447 2452 2457 2462 2467 2472 2484[DISABLED]
nl80211: Mode IEEE 802.11a: 5180 5200 5220 5240 5260[NO_IR][RADAR] 5280[NO_IR][RADAR] 5300[NO_IR][RADAR] 5320[NO_IR][RADAR] 5500[NO_IR][RADAR] 5520[NO_IR][RADAR] 5540[NO_IR][RADAR] 5560[NO_IR][RADAR] 5580[NO_IR][RADAR]

Is Mode IEEE 802.11ac missing?

2. nl80211: kernel reports: Channel is disabled
nl80211: Failed to set channel (freq=5210): -22 (Invalid argument)

This is from my wireless card:
$ iw phy #0 reg get
...
Frequencies:
                        * 5180 MHz [36] (30.0 dBm)
                        * 5200 MHz [40] (30.0 dBm)
                        * 5220 MHz [44] (30.0 dBm)
                        * 5240 MHz [48] (30.0 dBm)
                        * 5260 MHz [52] (30.0 dBm) (no IR, radar detection)
                        * 5280 MHz [56] (30.0 dBm) (no IR, radar detection)
                        * 5300 MHz [60] (30.0 dBm) (no IR, radar detection)
                        * 5320 MHz [64] (30.0 dBm) (no IR, radar detection)
                        * 5500 MHz [100] (30.0 dBm) (no IR, radar detection)
                        * 5520 MHz [104] (30.0 dBm) (no IR, radar detection)
                        * 5540 MHz [108] (30.0 dBm) (no IR, radar detection)
                        * 5560 MHz [112] (30.0 dBm) (no IR, radar detection)
                        * 5580 MHz [116] (30.0 dBm) (no IR, radar detection)
                        * 5600 MHz [120] (disabled)
                        * 5620 MHz [124] (disabled)
                        * 5640 MHz [128] (disabled)
                        * 5660 MHz [132] (30.0 dBm) (no IR, radar detection)
                        * 5680 MHz [136] (30.0 dBm) (no IR, radar detection)
                        * 5700 MHz [140] (30.0 dBm) (no IR, radar detection)
                        * 5720 MHz [144] (30.0 dBm) (no IR, radar detection)
                        * 5745 MHz [149] (30.0 dBm)
                        * 5765 MHz [153] (30.0 dBm)
                        * 5785 MHz [157] (30.0 dBm)
                        * 5805 MHz [161] (30.0 dBm)
                        * 5825 MHz [165] (30.0 dBm)
                        * 5845 MHz [169] (disabled)
                        * 5865 MHz [173] (disabled)
                        * 5885 MHz [177] (disabled)

---

### Post by him610 on 2020-03-01
Hello bjlockie,
Looks like you are in Canada from the country code. 
Are you trying to set up your Access Point on one of your computers, or what?

May I offer some advice? You are much more likely to get a helpful response.
Folks are encouraged to complete the steps here, [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108") before posting.
Use code tags to encapsulate both the command used as well as the complete response.

---

