---
title: "Wireless suddenly stopped working (restarting doesn't help)"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by 9-me-1 on 2014-01-22
Yesterday morning, the bulit-in wireless card on my laptop (wlan0) suddenly stopped working. Luckily I had a usb wifi-stick handy (wlan1), so I can still access internet.

I've googled around for hours without finding a solution. I'm attaching all the various logfiles I've heard mentioned, in the hope that one of you experienced guys can help me solve this.

Firstly, **syslog | grep wlan0 **(the wireless card in question), from the morning when it happened. 
```

Jan 21 09:50:49 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with 08:ea:44:89:b0:98 (SSID='EpicWifi' freq=2412 MHz)
Jan 21 09:50:49 ComputerName kernel: [ 1647.460029] wlan0: authenticate with 08:ea:44:89:b0:98
Jan 21 09:50:49 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-DISCONNECTED bssid=08:ea:44:89:b0:98 reason=1
Jan 21 09:50:49 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID E0:1C:41:61:78:18 (EpicWifi) to (none) ((none))
Jan 21 09:50:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: completed -> authenticating
Jan 21 09:50:49 ComputerName kernel: [ 1647.476214] wlan0: direct probe to 08:ea:44:89:b0:98 (try 1/3)
Jan 21 09:50:50 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:50:50 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 09:50:50 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan 21 09:50:50 ComputerName kernel: [ 1648.095724] wlan0: direct probe to 08:ea:44:89:b0:98 (try 2/3)
Jan 21 09:50:50 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 09:50:50 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:25:ea:d8 (SSID='EpicWifi' freq=2472 MHz)
Jan 21 09:50:50 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 09:50:50 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan 21 09:50:50 ComputerName kernel: [ 1648.299773] wlan0: direct probe to 08:ea:44:89:b0:98 (try 3/3)
Jan 21 09:50:50 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 09:50:51 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:58 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:50:51 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 09:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan 21 09:50:51 ComputerName kernel: [ 1649.301090] wlan0: authentication with 08:ea:44:89:b0:98 timed out
Jan 21 09:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 09:50:51 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with 08:ea:44:89:b0:98 (SSID='EpicWifi' freq=2412 MHz)
Jan 21 09:50:51 ComputerName kernel: [ 1649.674761] wlan0: authenticate with 08:ea:44:89:b0:98
Jan 21 09:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 21 09:50:51 ComputerName kernel: [ 1649.705480] wlan0: direct probe to 08:ea:44:89:b0:98 (try 1/3)
Jan 21 09:50:52 ComputerName kernel: [ 1649.909477] wlan0: direct probe to 08:ea:44:89:b0:98 (try 2/3)
Jan 21 09:50:52 ComputerName kernel: [ 1650.113681] wlan0: direct probe to 08:ea:44:89:b0:98 (try 3/3)
Jan 21 09:50:52 ComputerName kernel: [ 1650.317885] wlan0: authentication with 08:ea:44:89:b0:98 timed out
Jan 21 09:50:52 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan 21 09:50:53 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 09:50:53 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:50:53 ComputerName kernel: [ 1651.380511] wlan0: authenticate with e0:1c:41:61:78:18
Jan 21 09:50:53 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 21 09:50:53 ComputerName kernel: [ 1651.411342] wlan0: send auth to e0:1c:41:61:78:18 (try 1/3)
Jan 21 09:50:53 ComputerName kernel: [ 1651.422830] wlan0: authenticated
Jan 21 09:50:53 ComputerName wpa_supplicant[882]: wlan0: Trying to associate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:50:53 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 21 09:50:53 ComputerName kernel: [ 1651.426920] wlan0: associate with e0:1c:41:61:78:18 (try 1/3)
Jan 21 09:50:53 ComputerName wpa_supplicant[882]: wlan0: Associated with e0:1c:41:61:78:18
Jan 21 09:50:53 ComputerName kernel: [ 1651.431220] wlan0: RX AssocResp from e0:1c:41:61:78:18 (capab=0x31 status=0 aid=3)
Jan 21 09:50:53 ComputerName kernel: [ 1651.431471] wlan0: associated
Jan 21 09:50:53 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 21 09:50:53 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 21 09:50:53 ComputerName wpa_supplicant[882]: wlan0: WPA: Key negotiation completed with e0:1c:41:61:78:18 [PTK=CCMP GTK=CCMP]
Jan 21 09:50:53 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-CONNECTED - Connection to e0:1c:41:61:78:18 completed (reauth) [id=0 id_str=]
Jan 21 09:50:53 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan 21 09:50:53 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID (none) ((none)) to E0:1C:41:61:78:18 (EpicWifi)
Jan 21 09:54:49 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:50:58 (SSID='EpicWifi' freq=2452 MHz)
Jan 21 09:54:49 ComputerName kernel: [ 1887.407792] wlan0: authenticate with e0:1c:41:61:50:58
Jan 21 09:54:49 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-DISCONNECTED bssid=e0:1c:41:61:50:58 reason=1
Jan 21 09:54:49 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID E0:1C:41:61:78:18 (EpicWifi) to (none) ((none))
Jan 21 09:54:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: completed -> authenticating
Jan 21 09:54:49 ComputerName kernel: [ 1887.423974] wlan0: direct probe to e0:1c:41:61:50:58 (try 1/3)
Jan 21 09:54:49 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:54:49 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 09:54:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan 21 09:54:49 ComputerName kernel: [ 1887.971907] wlan0: send auth to e0:1c:41:61:50:58 (try 2/3)
Jan 21 09:54:49 ComputerName kernel: [ 1887.974181] wlan0: authenticated
Jan 21 09:54:50 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 09:54:51 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:54:51 ComputerName kernel: [ 1889.021064] wlan0: authenticate with e0:1c:41:61:78:18
Jan 21 09:54:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 21 09:54:51 ComputerName wpa_supplicant[882]: wlan0: Trying to associate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:54:51 ComputerName kernel: [ 1889.037299] wlan0: send auth to e0:1c:41:61:78:18 (try 1/3)
Jan 21 09:54:51 ComputerName kernel: [ 1889.039694] wlan0: authenticated
Jan 21 09:54:51 ComputerName kernel: [ 1889.040784] wlan0: associate with e0:1c:41:61:78:18 (try 1/3)
Jan 21 09:54:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 21 09:54:51 ComputerName wpa_supplicant[882]: wlan0: Associated with e0:1c:41:61:78:18
Jan 21 09:54:51 ComputerName kernel: [ 1889.046676] wlan0: RX AssocResp from e0:1c:41:61:78:18 (capab=0x31 status=0 aid=2)
Jan 21 09:54:51 ComputerName kernel: [ 1889.046907] wlan0: associated
Jan 21 09:54:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan 21 09:54:51 ComputerName wpa_supplicant[882]: wlan0: WPA: Key negotiation completed with e0:1c:41:61:78:18 [PTK=CCMP GTK=CCMP]
Jan 21 09:54:51 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-CONNECTED - Connection to e0:1c:41:61:78:18 completed (reauth) [id=0 id_str=]
Jan 21 09:54:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan 21 09:54:51 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID (none) ((none)) to E0:1C:41:61:78:18 (EpicWifi)
Jan 21 09:56:49 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:58 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:56:49 ComputerName kernel: [ 2007.532372] wlan0: authenticate with e0:1c:41:61:78:58
Jan 21 09:56:49 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-DISCONNECTED bssid=e0:1c:41:61:78:58 reason=1
Jan 21 09:56:49 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID E0:1C:41:61:78:18 (EpicWifi) to (none) ((none))
Jan 21 09:56:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: completed -> authenticating
Jan 21 09:56:49 ComputerName kernel: [ 2007.548638] wlan0: send auth to e0:1c:41:61:78:58 (try 1/3)
Jan 21 09:56:49 ComputerName wpa_supplicant[882]: wlan0: Trying to associate with e0:1c:41:61:78:58 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:56:49 ComputerName kernel: [ 2007.578300] wlan0: authenticated
Jan 21 09:56:49 ComputerName kernel: [ 2007.579547] wlan0: associate with e0:1c:41:61:78:58 (try 1/3)
Jan 21 09:56:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 21 09:56:49 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 09:56:49 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 09:56:49 ComputerName kernel: [ 2007.791826] wlan0: associate with e0:1c:41:61:78:58 (try 2/3)
Jan 21 09:56:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jan 21 09:56:49 ComputerName wpa_supplicant[882]: wlan0: Associated with e0:1c:41:61:78:58
Jan 21 09:56:49 ComputerName kernel: [ 2007.853284] wlan0: RX AssocResp from e0:1c:41:61:78:58 (capab=0x431 status=0 aid=4)
Jan 21 09:56:49 ComputerName kernel: [ 2007.853518] wlan0: associated
Jan 21 09:56:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> 4-way handshake
Jan 21 09:56:49 ComputerName wpa_supplicant[882]: wlan0: WPA: Key negotiation completed with e0:1c:41:61:78:58 [PTK=CCMP GTK=CCMP]
Jan 21 09:56:49 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-CONNECTED - Connection to e0:1c:41:61:78:58 completed (reauth) [id=0 id_str=]
Jan 21 09:56:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan 21 09:56:49 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID (none) ((none)) to E0:1C:41:61:78:58 (EpicWifi)
Jan 21 10:12:49 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:50:58 (SSID='EpicWifi' freq=2452 MHz)
Jan 21 10:12:49 ComputerName kernel: [ 2968.494440] wlan0: authenticate with e0:1c:41:61:50:58
Jan 21 10:12:49 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-DISCONNECTED bssid=e0:1c:41:61:50:58 reason=1
Jan 21 10:12:49 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID E0:1C:41:61:78:58 (EpicWifi) to (none) ((none))
Jan 21 10:12:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: completed -> authenticating
Jan 21 10:12:49 ComputerName kernel: [ 2968.510590] wlan0: direct probe to e0:1c:41:61:50:58 (try 1/3)
Jan 21 10:12:49 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:58 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 10:12:49 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 10:12:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan 21 10:12:49 ComputerName kernel: [ 2969.058288] wlan0: direct probe to e0:1c:41:61:50:58 (try 2/3)
Jan 21 10:12:50 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 10:12:51 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:50:58 (SSID='EpicWifi' freq=2452 MHz)
Jan 21 10:12:51 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 10:12:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan 21 10:12:51 ComputerName kernel: [ 2970.091467] wlan0: send auth to e0:1c:41:61:50:58 (try 3/3)
Jan 21 10:12:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 10:12:51 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:58 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 10:12:51 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 10:12:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan 21 10:12:51 ComputerName kernel: [ 2970.263535] wlan0: authentication with e0:1c:41:61:50:58 timed out
Jan 21 10:12:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 10:12:51 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 10:12:51 ComputerName kernel: [ 2970.420582] wlan0: authenticate with e0:1c:41:61:78:18
Jan 21 10:12:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 21 10:12:51 ComputerName kernel: [ 2970.451930] wlan0: send auth to e0:1c:41:61:78:18 (try 1/3)
Jan 21 10:12:51 ComputerName wpa_supplicant[882]: wlan0: Trying to associate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 10:12:51 ComputerName kernel: [ 2970.499932] wlan0: authenticated
Jan 21 10:12:51 ComputerName kernel: [ 2970.503572] wlan0: associate with e0:1c:41:61:78:18 (try 1/3)
Jan 21 10:12:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 21 10:12:51 ComputerName kernel: [ 2970.507157] wlan0: RX AssocResp from e0:1c:41:61:78:18 (capab=0x431 status=0 aid=2)
Jan 21 10:12:51 ComputerName kernel: [ 2970.507401] wlan0: associated
Jan 21 10:12:51 ComputerName wpa_supplicant[882]: wlan0: Associated with e0:1c:41:61:78:18
Jan 21 10:12:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan 21 10:12:51 ComputerName wpa_supplicant[882]: wlan0: WPA: Key negotiation completed with e0:1c:41:61:78:18 [PTK=CCMP GTK=CCMP]
Jan 21 10:12:51 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-CONNECTED - Connection to e0:1c:41:61:78:18 completed (reauth) [id=0 id_str=]
Jan 21 10:12:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan 21 10:12:51 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID (none) ((none)) to E0:1C:41:61:78:18 (EpicWifi)
Jan 21 10:50:49 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:25:ea:d8 (SSID='EpicWifi' freq=2472 MHz)
Jan 21 10:50:49 ComputerName kernel: [ 5250.759099] wlan0: authenticate with e0:1c:41:25:ea:d8
Jan 21 10:50:49 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-DISCONNECTED bssid=e0:1c:41:25:ea:d8 reason=1
Jan 21 10:50:49 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID E0:1C:41:61:78:18 (EpicWifi) to (none) ((none))
Jan 21 10:50:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: completed -> authenticating
Jan 21 10:50:49 ComputerName kernel: [ 5250.775286] wlan0: direct probe to e0:1c:41:25:ea:d8 (try 1/3)
Jan 21 10:50:49 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 10:50:49 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 10:50:49 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan 21 10:50:49 ComputerName kernel: [ 5251.323092] wlan0: direct probe to e0:1c:41:25:ea:d8 (try 2/3)
Jan 21 10:50:50 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 10:50:50 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:25:ea:d8 (SSID='EpicWifi' freq=2472 MHz)
Jan 21 10:50:50 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 10:50:50 ComputerName kernel: [ 5252.340327] wlan0: direct probe to e0:1c:41:25:ea:d8 (try 3/3)
Jan 21 10:50:50 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan 21 10:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 10:50:51 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:78:18 (SSID='EpicWifi' freq=2432 MHz)
Jan 21 10:50:51 ComputerName wpa_supplicant[882]: wlan0: SME: Authentication request to the driver failed
Jan 21 10:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Jan 21 10:50:51 ComputerName kernel: [ 5252.600436] wlan0: authentication with e0:1c:41:25:ea:d8 timed out
Jan 21 10:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 21 10:50:51 ComputerName wpa_supplicant[882]: wlan0: SME: Trying to authenticate with e0:1c:41:61:50:58 (SSID='EpicWifi' freq=2452 MHz)
Jan 21 10:50:51 ComputerName kernel: [ 5252.830058] wlan0: authenticate with e0:1c:41:61:50:58
Jan 21 10:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 21 10:50:51 ComputerName kernel: [ 5252.860794] wlan0: send auth to e0:1c:41:61:50:58 (try 1/3)
Jan 21 10:50:51 ComputerName wpa_supplicant[882]: wlan0: Trying to associate with e0:1c:41:61:50:58 (SSID='EpicWifi' freq=2452 MHz)
Jan 21 10:50:51 ComputerName kernel: [ 5252.864447] wlan0: authenticated
Jan 21 10:50:51 ComputerName kernel: [ 5252.868429] wlan0: associate with e0:1c:41:61:50:58 (try 1/3)
Jan 21 10:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 21 10:50:51 ComputerName wpa_supplicant[882]: wlan0: Associated with e0:1c:41:61:50:58
Jan 21 10:50:51 ComputerName kernel: [ 5252.876826] wlan0: RX AssocResp from e0:1c:41:61:50:58 (capab=0x431 status=0 aid=6)
Jan 21 10:50:51 ComputerName kernel: [ 5252.877073] wlan0: associated
Jan 21 10:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 21 10:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan 21 10:50:51 ComputerName wpa_supplicant[882]: wlan0: WPA: Key negotiation completed with e0:1c:41:61:50:58 [PTK=CCMP GTK=CCMP]
Jan 21 10:50:51 ComputerName wpa_supplicant[882]: wlan0: CTRL-EVENT-CONNECTED - Connection to e0:1c:41:61:50:58 completed (reauth) [id=0 id_str=]
Jan 21 10:50:51 ComputerName NetworkManager[811]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jan 21 10:50:51 ComputerName NetworkManager[811]: <info> (wlan0): roamed from BSSID (none) ((none)) to E0:1C:41:61:50:58 (EpicWifi)
Jan 21 10:52:36 ComputerName NetworkManager[781]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0)
Jan 21 10:52:36 ComputerName NetworkManager[781]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 21 10:52:36 ComputerName NetworkManager[781]: <info> (wlan0): using nl80211 for WiFi device control
Jan 21 10:52:36 ComputerName NetworkManager[781]: <info> (wlan0): driver supports Access Point (AP) mode
Jan 21 10:52:36 ComputerName NetworkManager[781]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8723ae' ifindex: 3)
Jan 21 10:52:36 ComputerName NetworkManager[781]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 21 10:52:36 ComputerName NetworkManager[781]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 21 10:52:36 ComputerName NetworkManager[781]: <info> (wlan0): bringing up device.
Jan 21 10:52:37 ComputerName NetworkManager[781]: <info> (wlan0): preparing device.
Jan 21 10:52:37 ComputerName NetworkManager[781]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 21 10:52:37 ComputerName kernel: [    5.220404] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 10:52:37 ComputerName kernel: [    5.220647] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 10:52:37 ComputerName NetworkManager[781]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:52:37 ComputerName NetworkManager[781]: <info> (wlan0): supplicant interface state: starting -> ready
Jan 21 10:52:37 ComputerName NetworkManager[781]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 21 10:52:37 ComputerName NetworkManager[781]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan 21 10:52:37 ComputerName NetworkManager[781]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:55:25 ComputerName NetworkManager[781]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Jan 21 10:55:25 ComputerName NetworkManager[781]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 21 10:55:25 ComputerName NetworkManager[781]: <info> (wlan0): taking down device.
Jan 21 10:55:28 ComputerName NetworkManager[781]: <info> (wlan0): bringing up device.
Jan 21 10:55:28 ComputerName NetworkManager[781]: <info> (wlan0): bringing up device.
Jan 21 10:55:28 ComputerName kernel: [  176.817446] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 10:55:28 ComputerName NetworkManager[781]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:55:28 ComputerName NetworkManager[781]: <info> (wlan0): supplicant interface state: starting -> ready
Jan 21 10:55:28 ComputerName NetworkManager[781]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 21 10:55:28 ComputerName NetworkManager[781]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan 21 10:55:28 ComputerName NetworkManager[781]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:55:47 ComputerName NetworkManager[781]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Jan 21 10:55:47 ComputerName NetworkManager[781]: <info> (wlan0): cleaning up...
Jan 21 10:55:47 ComputerName NetworkManager[781]: <info> (wlan0): taking down device.
Jan 21 10:55:49 ComputerName NetworkManager[781]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 21 10:55:49 ComputerName NetworkManager[781]: <info> (wlan0): bringing up device.
Jan 21 10:55:50 ComputerName NetworkManager[781]: <info> (wlan0): preparing device.
Jan 21 10:55:50 ComputerName NetworkManager[781]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 21 10:55:50 ComputerName kernel: [  198.601280] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 10:55:50 ComputerName NetworkManager[781]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:55:50 ComputerName NetworkManager[781]: <info> (wlan0): supplicant interface state: starting -> ready
Jan 21 10:55:50 ComputerName NetworkManager[781]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 21 10:55:50 ComputerName NetworkManager[781]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan 21 10:55:50 ComputerName NetworkManager[781]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:56:31 ComputerName NetworkManager[746]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0)
Jan 21 10:56:31 ComputerName NetworkManager[746]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): using nl80211 for WiFi device control
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): driver supports Access Point (AP) mode
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8723ae' ifindex: 3)
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): bringing up device.
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): preparing device.
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 21 10:56:31 ComputerName kernel: [    4.954484] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 10:56:31 ComputerName kernel: [    4.954756] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): supplicant interface state: starting -> ready
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan 21 10:56:31 ComputerName NetworkManager[746]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:57:18 ComputerName NetworkManager[757]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0)
Jan 21 10:57:18 ComputerName NetworkManager[757]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): using nl80211 for WiFi device control
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): driver supports Access Point (AP) mode
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8723ae' ifindex: 2)
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): bringing up device.
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): preparing device.
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 21 10:57:18 ComputerName kernel: [    4.983948] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 10:57:18 ComputerName kernel: [    4.984208] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: starting -> ready
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan 21 10:57:18 ComputerName NetworkManager[757]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> Activation (wlan0) starting connection 'EpicWifi'
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> Activation (wlan0/wireless): connection 'EpicWifi' has security, and secrets exist.  No new secrets needed.
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 21 10:57:34 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jan 21 10:57:59 ComputerName NetworkManager[757]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jan 21 10:57:59 ComputerName NetworkManager[757]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jan 21 10:57:59 ComputerName NetworkManager[757]: <warn> Activation (wlan0) failed for connection 'EpicWifi'
Jan 21 10:57:59 ComputerName NetworkManager[757]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 21 10:57:59 ComputerName NetworkManager[757]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 21 10:58:00 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: scanning -> inactive
Jan 21 10:58:08 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: inactive -> disabled
Jan 21 10:58:14 ComputerName kernel: [   60.971879] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 10:58:14 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: disabled -> inactive
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) starting connection 'EpicWifi'
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0/wireless): access point 'EpicWifi' has security, but secrets are required.
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0/wireless): connection 'EpicWifi' has security, and secrets exist.  No new secrets needed.
Jan 21 10:58:33 ComputerName NetworkManager[757]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 21 10:58:34 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jan 21 10:58:58 ComputerName NetworkManager[757]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jan 21 10:58:58 ComputerName NetworkManager[757]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Jan 21 10:58:58 ComputerName NetworkManager[757]: <warn> Activation (wlan0) failed for connection 'EpicWifi'
Jan 21 10:58:58 ComputerName NetworkManager[757]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 21 10:58:58 ComputerName NetworkManager[757]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 21 10:58:59 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: scanning -> inactive
Jan 21 11:02:35 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: inactive -> disabled
Jan 21 11:05:15 ComputerName kernel: [  480.090091] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 11:05:15 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: disabled -> inactive
Jan 21 13:14:06 ComputerName NetworkManager[757]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Jan 21 13:14:06 ComputerName NetworkManager[757]: <info> (wlan0): cleaning up...
Jan 21 13:14:06 ComputerName NetworkManager[757]: <info> (wlan0): taking down device.
Jan 21 14:40:28 ComputerName NetworkManager[757]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 21 14:40:28 ComputerName NetworkManager[757]: <info> (wlan0): bringing up device.
Jan 21 14:40:28 ComputerName NetworkManager[757]: <info> (wlan0): preparing device.
Jan 21 14:40:28 ComputerName NetworkManager[757]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 21 14:40:28 ComputerName kernel: [ 8214.443526] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 14:47:27 ComputerName NetworkManager[757]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0)
Jan 21 14:47:27 ComputerName NetworkManager[757]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): using nl80211 for WiFi device control
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): driver supports Access Point (AP) mode
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8723ae' ifindex: 3)
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): bringing up device.
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): preparing device.
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 21 14:47:27 ComputerName kernel: [    5.020309] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 14:47:27 ComputerName kernel: [    5.020567] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0) supports 4 scan SSIDs
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: starting -> ready
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan 21 14:47:27 ComputerName NetworkManager[757]: <info> (wlan0) supports 4 scan SSIDs

```

Secondly, output of **sudo lshw -C network**:

```

  *-network
       description: Wireless interface
       product: RTL8723AE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 6c:71:d9:9a:0f:c3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723ae driverversion=3.11.0-15-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:e000(size=256) memory:f7c00000-f7c03fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:2
       logical name: wlan1
       serial: bc:05:43:04:11:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.11.0-15-generic firmware=1.3 ip=192.168.2.178 link=yes multicast=yes wireless=IEEE 802.11bgn

```

Thirdly, output of **iwconfig **(again, **wlan0** is the device in question):

```

wlan1     IEEE 802.11bgn  ESSID:"EpicWifi"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: E0:1C:41:61:50:54   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:1029   Missed beacon:0

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

```

Output of **lsmod**:
```

Module                  Size  Used by
usb_storage            62062  0 
parport_pc             32701  0 
ppdev                  17671  0 
rfcomm                 69130  12 
bnep                   19704  2 
snd_hda_codec_hdmi     41117  1 
snd_hda_codec_realtek    55704  1 
joydev                 17377  0 
ath9k_htc              95884  0 
ath9k_common           13859  1 ath9k_htc
hid_generic            12548  0 
uvcvideo               80885  0 
ath9k_hw              444732  2 ath9k_common,ath9k_htc
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
usbhid                 53014  0 
videobuf2_core         40499  1 uvcvideo
hid                   105858  2 hid_generic,usbhid
ath                    23827  3 ath9k_common,ath9k_htc,ath9k_hw
videodev              133509  2 uvcvideo,videobuf2_core
btusb                  28267  0 
bluetooth             372041  22 bnep,btusb,rfcomm
x86_pkg_temp_thermal    14162  0 
kvm_intel             138567  0 
kvm                   431720  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
arc4                   12608  4 
microcode              23576  0 
snd_hda_intel          48171  5 
rtl8723ae              86524  0 
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
rtl_pci                26641  1 rtl8723ae
snd_hwdep              13602  1 snd_hda_codec
rtlwifi                63229  2 rtl_pci,rtl8723ae
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              597268  4 rtl_pci,rtlwifi,ath9k_htc,rtl8723ae
psmouse                97655  0 
snd_rawmidi            30095  1 snd_seq_midi
serio_raw              13413  0 
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
cfg80211              480503  4 ath,mac80211,rtlwifi,ath9k_htc
mei_me                 18421  0 
lpc_ich                21080  0 
i915                  661261  5 
mei                    77782  1 mei_me
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm_kms_helper         52710  1 i915
soundcore              12680  1 snd
wmi                    19070  0 
drm                   297056  4 i915,drm_kms_helper
video                  19318  1 i915
coretemp               13435  0 
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ahci                   25819  3 
libahci                31928  1 ahci

```

**iwlist scan **(irrelevant part cut out):
```

lo        Interface doesn't support scanning.

wlan0     No scan results

```

Update: Adding output of **rfkill list all:**

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
8: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
9: phy4: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

