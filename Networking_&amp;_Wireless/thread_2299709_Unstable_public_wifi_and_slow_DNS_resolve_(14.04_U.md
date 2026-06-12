---
title: "Unstable public wifi and slow DNS resolve (14.04 Ubuntu)"
date: 2015-10-20
forum: Networking &amp; Wireless
---

### Post by mistcloud-misty on 2015-10-20
Significant details of lspci command:
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)

03:00.0 Network controller: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter

```

My home Wifi network has no connection problems. It is a WPA/WPA2 personal network that has a password to login. 

On the other hand, my campus's public wifi is pretty awful. It isn't secure, but it has a special login for the first use: it redirects your first link when connected to login with your campus username and password, then requires a restart to work. Not that was done awhile ago. Unfortunately the wifi, even with full bars of connectivity, is constantly disconnecting. Sometimes it reconnects immediately, sometimes it doesn't. Sometimes it doesn't reconnect until I disable networking then re-enable it or restart, but it will always have some problem, whether connected for awhile or not. 

Checking the syslog, I have a few areas of information about it. 
```
Oct 20 13:02:08 arcane-X555LB dbus[783]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Oct 20 13:02:08 arcane-X555LB NetworkManager[1033]: <info> wpa_supplicant started
Oct 20 13:02:08 arcane-X555LB wpa_supplicant[3928]: Successfully initialized wpa_supplicant
Oct 20 13:02:18 arcane-X555LB NetworkManager[1033]: <info> (wlan0): supplicant interface state: init -> starting
Oct 20 13:02:18 arcane-X555LB NetworkManager[1033]: <info> wpa_supplicant die count reset
Oct 20 13:02:18 arcane-X555LB NetworkManager[1033]: <info> (wlan0) supports 4 scan SSIDs
Oct 20 13:02:18 arcane-X555LB NetworkManager[1033]: <info> (wlan0): supplicant interface state: starting -> ready
Oct 20 13:02:18 arcane-X555LB NetworkManager[1033]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Oct 20 13:02:18 arcane-X555LB NetworkManager[1033]: <warn> Trying to remove a non-existant call id.
Oct 20 13:02:18 arcane-X555LB wpa_supplicant[3929]: wlan0: Reject scan trigger since one is already pending
Oct 20 13:02:18 arcane-X555LB NetworkManager[1033]: <info> (wlan0): supplicant interface state: ready -> disconnected
Oct 20 13:02:18 arcane-X555LB NetworkManager[1033]: <info> (wlan0) supports 4 scan SSIDs
Oct 20 13:02:18 arcane-X555LB wpa_supplicant[3929]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Auto-activating connection 'tempest'.
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Activation (wlan0) starting connection 'tempest'
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> NetworkManager state is now CONNECTING
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Activation (wlan0/wireless): connection 'tempest' requires no security.  No secrets needed.
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Config: added 'ssid' value 'tempest'
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Config: added 'scan_ssid' value '1'
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Config: added 'key_mgmt' value 'NONE'
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> Config: set interface ap_scan to 1
Oct 20 13:02:20 arcane-X555LB wpa_supplicant[3929]: wlan0: SME: Trying to authenticate with 00:18:74:fb:08:00 (SSID='tempest' freq=2462 MHz)
Oct 20 13:02:20 arcane-X555LB kernel: [  208.030704] wlan0: authenticate with 00:18:74:fb:08:00
Oct 20 13:02:20 arcane-X555LB NetworkManager[1033]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Oct 20 13:02:20 arcane-X555LB wpa_supplicant[3929]: wlan0: Trying to associate with 00:18:74:fb:08:00 (SSID='tempest' freq=2462 MHz)
Oct 20 13:02:20 arcane-X555LB kernel: [  208.038688] wlan0: send auth to 00:18:74:fb:08:00 (try 1/3)
Oct 20 13:02:20 arcane-X555LB kernel: [  208.041687] wlan0: authenticated
Oct 20 13:02:20 arcane-X555LB kernel: [  208.042601] wlan0: associate with 00:18:74:fb:08:00 (try 1/3)
Oct 20 13:02:20 arcane-X555LB kernel: [  208.045470] wlan0: RX AssocResp from 00:18:74:fb:08:00 (capab=0x421 status=0 aid=5)
Oct 20 13:02:20 arcane-X555LB kernel: [  208.045483] ===>rt2800_sta_add:MT7630
Oct 20 13:02:20 arcane-X555LB kernel: [  208.045501] ===>rt2800_sta_add:MT7630   wcid=33
Oct 20 13:02:20 arcane-X555LB kernel: [  208.045502] Connect to AP MAC: 00:18:74:fb:08:00 WCID=33

```

```

Oct 20 13:02:44 arcane-X555LB wpa_supplicant[3929]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:18:74:fb:08:00 reason=4 locally_generated=1
Oct 20 13:02:44 arcane-X555LB NetworkManager[1033]: <warn> Connection disconnected (reason -4)
Oct 20 13:02:44 arcane-X555LB kernel: [  232.855737] cfg80211: Calling CRDA to update world regulatory domain
Oct 20 13:02:44 arcane-X555LB kernel: [  232.858008] cfg80211: World regulatory domain updated:
Oct 20 13:02:44 arcane-X555LB kernel: [  232.858011] cfg80211:  DFS Master region: unset
Oct 20 13:02:44 arcane-X555LB kernel: [  232.858013] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Oct 20 13:02:44 arcane-X555LB kernel: [  232.858015] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 20 13:02:44 arcane-X555LB kernel: [  232.858016] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 20 13:02:44 arcane-X555LB kernel: [  232.858017] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 20 13:02:44 arcane-X555LB kernel: [  232.858018] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 20 13:02:44 arcane-X555LB kernel: [  232.858019] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct 20 13:02:44 arcane-X555LB NetworkManager[1033]: <info> (wlan0): supplicant interface state: completed -> disconnected
Oct 20 13:02:44 arcane-X555LB wpa_supplicant[3929]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct 20 13:02:44 arcane-X555LB NetworkManager[1033]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct 20 13:02:45 arcane-X555LB wpa_supplicant[3929]: wlan0: SME: Trying to authenticate with 00:0e:38:3b:77:b0 (SSID='tempest' freq=2412 MHz)
Oct 20 13:02:45 arcane-X555LB kernel: [  233.084028] wlan0: authenticate with 00:0e:38:3b:77:b0
Oct 20 13:02:45 arcane-X555LB NetworkManager[1033]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 20 13:02:45 arcane-X555LB wpa_supplicant[3929]: wlan0: Trying to associate with 00:0e:38:3b:77:b0 (SSID='tempest' freq=2412 MHz)
Oct 20 13:02:45 arcane-X555LB kernel: [  233.099698] wlan0: send auth to 00:0e:38:3b:77:b0 (try 1/3)
Oct 20 13:02:45 arcane-X555LB kernel: [  233.101081] wlan0: authenticated
Oct 20 13:02:45 arcane-X555LB kernel: [  233.103563] wlan0: associate with 00:0e:38:3b:77:b0 (try 1/3)
Oct 20 13:02:45 arcane-X555LB NetworkManager[1033]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 20 13:02:45 arcane-X555LB kernel: [  233.106992] wlan0: RX AssocResp from 00:0e:38:3b:77:b0 (capab=0x421 status=0 aid=45)
Oct 20 13:02:45 arcane-X555LB kernel: [  233.107004] ===>rt2800_sta_add:MT7630
Oct 20 13:02:45 arcane-X555LB kernel: [  233.107022] ===>rt2800_sta_add:MT7630   wcid=33
```


Now, the other issue: the DNS resolving is extremely slow on all browsers, on all networks, and nothing I've read up on for fixes helps with my problem. In Google Chrome, if I click out of the loading tab, it will give me a resolution failed error until I click back on it to refresh it. The resolving is slow regardless of whether I have loaded up the page before already. 

Any input or help on either two problems would be appreciated, my searches haven't turned up anything of help! ):

Added the wireless-info.txt as attachment.

---

### Post by ian-weisser on 2015-10-20
Since you can get a solid connection at home, the culprit seems unlikely to be your Ubuntu system.

> ##### iwlist scan #######################

[...]

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

Perhaps a poorly-designed network. APs on the same channel may be interfering with each other at your location. Try moving a few seats over. Interference can be very localized.
The AP network may also be overloaded or misconfigured, forgetting or rejecting new connections.

---

### Post by mistcloud-misty on 2015-10-20
Unfortunately the problem occurs in every location I move to on campus, and does not seem to be worse or better at any spot.

---

### Post by Bucky Ball on 2015-10-20
Have you talked to the IT department on campus about this? They will know a lot more about why you're having problems on their network than we do. As above, as your connection at home is working fine it is not a problem at your end when you're on campus, unless you're entering the wrong details, which you appear not to be doing.

Possibly best to ask about slow DNS resolution on your home network on another thread as it doesn't appear related to your initial support question here (although fixing the DNS may improve your lumpy connection at uni but if you're getting good connection at home once resolved but not on campus, doubtful). Good luck. :)

---

