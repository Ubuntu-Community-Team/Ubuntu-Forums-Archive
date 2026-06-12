---
title: "Intel 6235 hostapd acs support?"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by i-steve-l on 2014-05-13
I am using an Intel 6235 WiFi/Bluetooth in a 3.0.35 kernel, and I've managed to get it working with hostapd by using the 'compat' or 'backport' package to use the iwlwifi driver. It works fine if I specify 'channel=1' or some other fixed channel in the hostapd.conf file, but if I try to use automatic channel selection (ACS) by specifying 'channel=0' then it tries to get survey data several times, but each time hostapd reports something like:

```
ACS: Scanning 4 / 5
wlan1: nl80211: scan request
nl80211: Scan frequency 2412 MHz
nl80211: Scan frequency 2417 MHz
nl80211: Scan frequency 2422 MHz
nl80211: Scan frequency 2427 MHz
nl80211: Scan frequency 2432 MHz
nl80211: Scan frequency 2437 MHz
nl80211: Scan frequency 2442 MHz
nl80211: Scan frequency 2447 MHz
nl80211: Scan frequency 2452 MHz
nl80211: Scan frequency 2457 MHz
nl80211: Scan frequency 2462 MHz
Scan requested (ret=0) - scan timeout 30 seconds
nl80211: Event message available
nl80211: Drv Event 33 (NL80211_CMD_TRIGGER_SCAN) received for wlan1
wlan1: nl80211: Scan trigger
wlan1: Event SCAN_STARTED (49) received
Unknown event 49
RTM_NEWLINK: ifi_index=4 ifname=wlan1 wext ifi_flags=0x1003 ([UP])
nl80211: Event message available
nl80211: Drv Event 34 (NL80211_CMD_NEW_SCAN_RESULTS) received for wlan1
wlan1: nl80211: New scan results available
nl80211: Scan included frequencies: 2412 2417 2422 2427 2432 2437 2442 2447 2452 2457 2462
wlan1: Event SCAN_RESULTS (3) received
ACS: Using survey based algorithm (acs_num_scans=5)
nl80211: Fetch survey data
wlan1: Event SURVEY (48) received
No survey data received

```

When it reaches the limit of the number of scans it is configured for, hostapd exits.

So, bottom line, does the Intel 6235 support ACS? If not, is this a limitation of the 6235 itself, the firmware (version 18.168.6.1), or the iwlwifi driver?

---

