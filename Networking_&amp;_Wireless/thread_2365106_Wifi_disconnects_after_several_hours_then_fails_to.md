---
title: "Wifi disconnects after several hours then fails to reconnect"
date: 2017-07-02
forum: Networking &amp; Wireless
---

### Post by ongdet on 2017-07-02
Hi, I have a server running Ubuntu 16.04.2 LTS (xenial) with the following wifi card: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express). The wifi connects without any problems at boot, but then randomly disconnects after a few hours or 1-2 days, probably due to my router acting up. My problem is that when it tries connecting again, it appears to succeed, but disconnects again immediately, leaving my server offline. I tried searching for the errors in the logs, but couldn't get closer to the root of the problem. I'd be grateful for any pointers as to how to get it reconnect successfully.

I see the following in syslog:
```

Jul  2 12:36:49 ... wpa_supplicant[1235]: wlp6s0: CTRL-EVENT-DISCONNECTED bssid=... reason=4 locally_generated=1
Jul  2 12:36:49 ... NetworkManager[956]: <warn>  [1498995409.6329] sup-iface[0x1e01a00,wlp6s0]: connection disconnected (reason -4)
Jul  2 12:36:49 ... wpa_supplicant[1235]: wlp6s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jul  2 12:36:49 ... kernel: [ 6247.705659] cfg80211: World regulatory domain updated:
Jul  2 12:36:49 ... kernel: [ 6247.705661] cfg80211:  DFS Master region: unset
Jul  2 12:36:49 ... kernel: [ 6247.705661] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul  2 12:36:49 ... kernel: [ 6247.705663] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:49 ... kernel: [ 6247.705664] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:49 ... kernel: [ 6247.705664] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:49 ... kernel: [ 6247.705665] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:49 ... kernel: [ 6247.705666] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Jul  2 12:36:49 ... kernel: [ 6247.705667] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Jul  2 12:36:49 ... kernel: [ 6247.705668] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:49 ... kernel: [ 6247.705668] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Jul  2 12:36:49 ... NetworkManager[956]: <info>  [1498995409.6536] device (wlp6s0): supplicant interface state: completed -> disconnected
Jul  2 12:36:49 ... NetworkManager[956]: <info>  [1498995409.7412] device (wlp6s0): supplicant interface state: disconnected -> scanning
Jul  2 12:36:50 ... wpa_supplicant[1235]: wlp6s0: SME: Trying to authenticate with ... (SSID='...' freq=2462 MHz)
Jul  2 12:36:50 ... kernel: [ 6248.532485] wlp6s0: authenticate with ...
Jul  2 12:36:50 ... NetworkManager[956]: <info>  [1498995410.5013] device (wlp6s0): supplicant interface state: scanning -> authenticating
Jul  2 12:36:50 ... kernel: [ 6248.556786] wlp6s0: send auth to ... (try 1/3)
Jul  2 12:36:50 ... wpa_supplicant[1235]: wlp6s0: Trying to associate with ... (SSID='...' freq=2462 MHz)
Jul  2 12:36:50 ... kernel: [ 6248.600905] wlp6s0: authenticated
Jul  2 12:36:50 ... kernel: [ 6248.603958] wlp6s0: associate with ... (try 1/3)
Jul  2 12:36:50 ... NetworkManager[956]: <info>  [1498995410.5505] device (wlp6s0): supplicant interface state: authenticating -> associating
Jul  2 12:36:50 ... wpa_supplicant[1235]: wlp6s0: Associated with ...
Jul  2 12:36:50 ... wpa_supplicant[1235]: wlp6s0: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=GB
Jul  2 12:36:50 ... kernel: [ 6248.646035] wlp6s0: RX AssocResp from ... (capab=0x411 status=0 aid=2)
Jul  2 12:36:50 ... kernel: [ 6248.646120] wlp6s0: associated
Jul  2 12:36:50 ... kernel: [ 6248.647661] cfg80211: Regulatory domain changed to country: GB
Jul  2 12:36:50 ... kernel: [ 6248.647663] cfg80211:  DFS Master region: ETSI
Jul  2 12:36:50 ... kernel: [ 6248.647664] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul  2 12:36:50 ... kernel: [ 6248.647665] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:50 ... kernel: [ 6248.647666] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:50 ... kernel: [ 6248.647667] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Jul  2 12:36:50 ... kernel: [ 6248.647668] cfg80211:   (5490000 KHz - 5710000 KHz @ 160000 KHz), (N/A, 2700 mBm), (0 s)
Jul  2 12:36:50 ... kernel: [ 6248.647669] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jul  2 12:36:50 ... NetworkManager[956]: <info>  [1498995410.5957] device (wlp6s0): supplicant interface state: associating -> associated
Jul  2 12:36:52 ... wpa_supplicant[1235]: wlp6s0: CTRL-EVENT-DISCONNECTED bssid=... reason=4 locally_generated=1
Jul  2 12:36:52 ... NetworkManager[956]: <warn>  [1498995412.6008] sup-iface[0x1e01a00,wlp6s0]: connection disconnected (reason -4)
Jul  2 12:36:52 ... wpa_supplicant[1235]: wlp6s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jul  2 12:36:52 ... kernel: [ 6250.658151] cfg80211: World regulatory domain updated:
Jul  2 12:36:52 ... kernel: [ 6250.658153] cfg80211:  DFS Master region: unset
Jul  2 12:36:52 ... kernel: [ 6250.658154] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul  2 12:36:52 ... kernel: [ 6250.658155] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:52 ... kernel: [ 6250.658156] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:52 ... kernel: [ 6250.658157] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:52 ... kernel: [ 6250.658158] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:52 ... kernel: [ 6250.658159] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Jul  2 12:36:52 ... kernel: [ 6250.658159] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Jul  2 12:36:52 ... kernel: [ 6250.658160] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:52 ... kernel: [ 6250.658161] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Jul  2 12:36:52 ... NetworkManager[956]: <info>  [1498995412.6059] device (wlp6s0): supplicant interface state: associated -> disconnected
Jul  2 12:36:52 ... NetworkManager[956]: <info>  [1498995412.7120] device (wlp6s0): supplicant interface state: disconnected -> scanning
Jul  2 12:36:53 ... wpa_supplicant[1235]: wlp6s0: SME: Trying to authenticate with ... (SSID='...' freq=2462 MHz)
Jul  2 12:36:53 ... kernel: [ 6251.504709] wlp6s0: authenticate with ...
Jul  2 12:36:53 ... NetworkManager[956]: <info>  [1498995413.4731] device (wlp6s0): supplicant interface state: scanning -> authenticating
Jul  2 12:36:53 ... kernel: [ 6251.528826] wlp6s0: send auth to ... (try 1/3)
Jul  2 12:36:53 ... wpa_supplicant[1235]: wlp6s0: Trying to associate with ... (SSID='...' freq=2462 MHz)
Jul  2 12:36:53 ... kernel: [ 6252.025840] wlp6s0: authenticated
Jul  2 12:36:53 ... kernel: [ 6252.028258] wlp6s0: associate with ... (try 1/3)
Jul  2 12:36:53 ... NetworkManager[956]: <info>  [1498995413.9753] device (wlp6s0): supplicant interface state: authenticating -> associating
Jul  2 12:36:53 ... wpa_supplicant[1235]: wlp6s0: Associated with ...
Jul  2 12:36:53 ... wpa_supplicant[1235]: wlp6s0: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=GB
Jul  2 12:36:53 ... kernel: [ 6252.046331] wlp6s0: RX AssocResp from ... (capab=0x411 status=0 aid=2)
Jul  2 12:36:53 ... kernel: [ 6252.046409] wlp6s0: associated
Jul  2 12:36:53 ... kernel: [ 6252.048117] cfg80211: Regulatory domain changed to country: GB
Jul  2 12:36:53 ... kernel: [ 6252.048119] cfg80211:  DFS Master region: ETSI
Jul  2 12:36:53 ... kernel: [ 6252.048119] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul  2 12:36:53 ... kernel: [ 6252.048121] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:53 ... kernel: [ 6252.048122] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Jul  2 12:36:53 ... kernel: [ 6252.048123] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Jul  2 12:36:53 ... kernel: [ 6252.048124] cfg80211:   (5490000 KHz - 5710000 KHz @ 160000 KHz), (N/A, 2700 mBm), (0 s)
Jul  2 12:36:53 ... kernel: [ 6252.048124] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jul  2 12:36:53 ... NetworkManager[956]: <info>  [1498995413.9958] device (wlp6s0): supplicant interface state: associating -> 4-way handshake
Jul  2 12:36:54 ... wpa_supplicant[1235]: wlp6s0: WPA: Key negotiation completed with ... [PTK=CCMP GTK=CCMP]
Jul  2 12:36:54 ... wpa_supplicant[1235]: wlp6s0: CTRL-EVENT-CONNECTED - Connection to ... completed [id=0 id_str=]
Jul  2 12:36:54 ... NetworkManager[956]: <info>  [1498995414.0460] device (wlp6s0): supplicant interface state: 4-way handshake -> completed
Jul  2 12:37:04 ... wpa_supplicant[1235]: wlp6s0: CTRL-EVENT-DISCONNECTED bssid=... reason=4 locally_generated=1
Jul  2 12:37:04 ... NetworkManager[956]: <warn>  [1498995424.6129] sup-iface[0x1e01a00,wlp6s0]: connection disconnected (reason -4)

```

PS The server makes an HTTP request every 2 minutes, so I'm not sure if the wifi would go into power saving mode.

Thank you!

---

### Post by johndough2 on 2017-07-03
Hi

Would a cable not be the answer?  Powerline adapters?

The WiFi would be enabled at boot up, hotplug or manual start?  

Edit your wlan0 config file?

What about bad packets, fragments causing a dis-connect.

The reg_dom seems to change prior to a disconnect, from GB to World, or am I wrong?

So is it a loss of WiFi or a loss to the server, or both?

---

### Post by ongdet on 2017-07-03
Hi,

I'd like to avoid using a cable if possible.

I configured wifi to be enabled automatically at boot, and it seems to work fine in that regard. Is there something specific I'd be modifying in the wlan0 config?

Yes, I saw the log lines re reg_dom but I don't know whether it's normal. Do you have some insight into this?

The server is fine but it loses its network connection. The wifi could have dropped out for a second, but all other devices (including a laptop running Debian) reconnected witout me noticing it.

Thanks!

---

### Post by johndough2 on 2017-07-03
Hi

No, and to make matters worse showing my stupidity, the error is

CTRL-EVENT-DISCONNECTED bssid=... reason=4 locally_generated=1
Jul  2 12:36:52 ... NetworkManager[956]: <warn>  [1498995412.6008] sup-iface[0x1e01a00,wlp6s0]: connection disconnected (reason -4)
Jul  2 12:36:52 ... wpa_supplicant[1235]: wlp6s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD

Suggesting that it is locally generated (internal?) reason -4; and not the regdom change I thought.

How about local interference, the WiFi is getting swamped by another signal and the throughtput rate drops, and the keepalive request fails.  As does any attempted reconnects.  AND if the signal swamping is short lived you ain't gonna catch it.

For windows I would use an early free version of inSSIDer, 
for linux perhaps [http://www.junauza.com/2011/01/network-security-linux-distros.html](http://www.junauza.com/2011/01/network-security-linux-distros.html)

and find some of the tools they use and use in your current distro hope they can produce a log file to supplement your own.

---

### Post by gordintoronto on 2017-07-04
If you're in a busy environment, such as an apartment building, changing the channel on the router might help. InSSIDer is a fabulous program, which, sadly, is not available for Linux.

My son lived in an apartment building, When he did a scan, he found 60 (!!) Wi-Fi networks.

---

