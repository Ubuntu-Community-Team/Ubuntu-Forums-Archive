---
title: "Problems with hostapd in 5GHz mode"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by joellarsonweb on 2014-01-02
I have been trying to setup a successful broadcast with hostapd in 5GHz mode (channel 36) and having problems doing so. I know that my device (Macbook Air 2011 11") has a Broadcom BCM43224 802.11abgn network controller.

I'm really not sure what the problem is at this point. I know I am able to broadcast on this channel when I am booted into OS X but not at all with Ubuntu. What is even stranger is that I have successfully gotten this to work one or twice using channel 161 and haven't been able to get it working since.

Here is my hostapd.conf:
```
[COLOR=#000000][FONT=Consolas]interface=wlan0
[/FONT][/COLOR]country_code=US
driver=nl80211
ssid=HostAPTest
hw_mode=a
channel=36
ieee80211n=1
wmm_ac_vo_acm=0
 
logger_syslog=-1
logger_syslog_level=0
logger_stdout=-1
logger_stdout_level=0
 
dump_file=/home/joel/Desktop/hostapd.dump
 
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=1234567890
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
[COLOR=#000000][FONT=Consolas]rsn_pairwise=CCMP[/FONT][/COLOR]
```

Here is the dump of the logging when I execute hostapd:
```
[COLOR=#000000][FONT=Consolas]joel@joel-MacBookAir:~$ sudo hostapd -dd /etc/hostapd/hostapd.conf [/FONT][/COLOR]random: Trying to read entropy from /dev/random
Configuration file: /etc/hostapd/hostapd.conf
nl80211: interface wlan0 in phy phy0
rfkill: initial event: idx=1 type=2 op=0 soft=0 hard=0
rfkill: initial event: idx=6 type=1 op=0 soft=0 hard=0
nl80211: Using driver-based off-channel TX
nl80211: Register frame command failed (type=208): ret=-114 (Operation already in progress)
nl80211: Register frame match - hexdump(len=2): 04 0a
nl80211: Failed to register Action frame processing - ignore for now
nl80211: Add own interface ifindex 45
nl80211: Set mode ifindex 45 iftype 3 (AP)
nl80211: Create interface iftype 6 (MONITOR)
nl80211: New interface mon.wlan0 created: ifindex=48
nl80211: Add own interface ifindex 48
BSS count 1, BSSID mask 00:00:00:00:00:00 (0 bits)
nl80211: Regulatory information - country=US
nl80211: 2402-2472 @ 40 MHz
nl80211: 5170-5250 @ 40 MHz
nl80211: 5250-5330 @ 40 MHz
nl80211: 5490-5600 @ 40 MHz
nl80211: 5650-5710 @ 40 MHz
nl80211: 5735-5835 @ 40 MHz
nl80211: 57240-63720 @ 2160 MHz
nl80211: Added 802.11b mode based on 802.11g information
Allowed channel: mode=1 chan=1 freq=2412 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=2 freq=2417 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=3 freq=2422 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=4 freq=2427 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=5 freq=2432 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=6 freq=2437 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=7 freq=2442 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=8 freq=2447 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=9 freq=2452 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=10 freq=2457 MHz max_tx_power=19 dBm
Allowed channel: mode=1 chan=11 freq=2462 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=1 freq=2412 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=2 freq=2417 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=3 freq=2422 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=4 freq=2427 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=5 freq=2432 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=6 freq=2437 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=7 freq=2442 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=8 freq=2447 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=9 freq=2452 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=10 freq=2457 MHz max_tx_power=19 dBm
Allowed channel: mode=0 chan=11 freq=2462 MHz max_tx_power=19 dBm
channel [0] (36) is disabled for use in AP mode, flags: 0x7
wlan0: IEEE 802.11 Configured channel (36) not found from the channel list of current mode (2) IEEE 802.11a
wlan0: IEEE 802.11 Hardware does not support configured channel
Could not select hw_mode and channel. (-4)
wlan0: Unable to setup interface.
Flushing old station entries
Deauthenticate all stations
nl80211: Remove interface ifindex=48
netlink: Operstate: linkmode=0, operstate=6
nl80211: Set mode ifindex 45 iftype 2 (STATION)
```

More debug information can be found at: [https://gist.github.com/JoelLarson/2632c0933a0cee5fc181](https://gist.github.com/JoelLarson/2632c0933a0cee5fc181)

Thanks!

---

