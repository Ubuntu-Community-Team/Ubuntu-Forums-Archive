---
title: "Ubuntu 14.04 LTS Network-Manager 0.9.8.8-0 and PEAP Enteprise unable to log on"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by Geir_Klamas on 2014-08-21
Hi..
I have problem connecting to wireless network with PEAP Enteprise auth. 
I have searched the net on this problem, and found the bug [#1104476]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1104476") and other links describing how to edit the /etc/NetworkManager/system-connections and editing the setting "system-ca-certs=true" to "false". 
I still have problems connecting to a wireless nettwork with PEAP and no cert.

I'm running Ubuntu 14.04 LTS and are up to date, on a Lenovo T540p.

> 
##### lspci #####

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 04)
    Subsystem: Lenovo Device [17aa:2210]
    Kernel driver in use: e1000e

04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
    Kernel driver in use: iwlwifi


> 
##### lsmod #####

iwlmvm                189774  0 
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  0 


```
 ##### Syslog #####

Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> NetworkManager state is now DISCONNECTED
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) starting connection 'ATEA'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> NetworkManager state is now CONNECTING
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 21 10:25:34 IBMT540p dbus[736]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <warn> Connection disconnected (reason -3)
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: completed -> disconnected
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <warn> Connection disconnected (reason -3)
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 21 10:25:34 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0/wireless): access point 'ATEA' has security, but secrets are required.
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 21 10:25:34 IBMT540p dbus[736]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0/wireless): connection 'ATEA' has security, and secrets exist.  No new secrets needed.
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'ssid' value 'ATEA'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'scan_ssid' value '1'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'key_mgmt' value 'WPA-EAP'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'auth_alg' value 'OPEN'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'password' value '<omitted>'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'eap' value 'PEAP'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'fragment_size' value '1300'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'identity' value 'one\geiklama'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'bgscan' value 'simple:30:-65:300'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: added 'proactive_key_caching' value '1'
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 21 10:25:34 IBMT540p NetworkManager[852]: <info> Config: set interface ap_scan to 1
Aug 21 10:25:36 IBMT540p avahi-daemon[845]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::ea2a:eaff:fe60:95aa.
Aug 21 10:25:36 IBMT540p avahi-daemon[845]: New relevant interface wlan0.IPv6 for mDNS.
Aug 21 10:25:36 IBMT540p avahi-daemon[845]: Registering new address record for fe80::ea2a:eaff:fe60:95aa on wlan0.*.
Aug 21 10:25:38 IBMT540p wpa_supplicant[982]: wlan0: SME: Trying to authenticate with 20:37:06:44:39:2b (SSID='ATEA' freq=5660 MHz)
Aug 21 10:25:38 IBMT540p kernel: [ 1617.118682] wlan0: authenticate with 20:37:06:44:39:2b
Aug 21 10:25:38 IBMT540p wpa_supplicant[982]: wlan0: Trying to associate with 20:37:06:44:39:2b (SSID='ATEA' freq=5660 MHz)
Aug 21 10:25:38 IBMT540p kernel: [ 1617.120644] wlan0: send auth to 20:37:06:44:39:2b (try 1/3)
Aug 21 10:25:38 IBMT540p kernel: [ 1617.121898] wlan0: authenticated
Aug 21 10:25:38 IBMT540p kernel: [ 1617.123169] wlan0: associate with 20:37:06:44:39:2b (try 1/3)
Aug 21 10:25:38 IBMT540p wpa_supplicant[982]: wlan0: Associated with 20:37:06:44:39:2b
Aug 21 10:25:38 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Aug 21 10:25:38 IBMT540p kernel: [ 1617.124548] wlan0: RX AssocResp from 20:37:06:44:39:2b (capab=0x111 status=0 aid=1)
Aug 21 10:25:38 IBMT540p kernel: [ 1617.125453] wlan0: associated
Aug 21 10:25:38 IBMT540p kernel: [ 1617.125495] cfg80211: Calling CRDA for country: NO
Aug 21 10:25:38 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: authenticating -> associated
Aug 21 10:25:38 IBMT540p kernel: [ 1617.128506] cfg80211: Regulatory domain changed to country: NO
Aug 21 10:25:38 IBMT540p kernel: [ 1617.128512] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 10:25:38 IBMT540p kernel: [ 1617.128514] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:38 IBMT540p kernel: [ 1617.128516] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:38 IBMT540p kernel: [ 1617.128518] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:38 IBMT540p kernel: [ 1617.128519] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Aug 21 10:25:38 IBMT540p kernel: [ 1617.128521] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Aug 21 10:25:39 IBMT540p kernel: [ 1617.962052] wlan0: deauthenticated from 20:37:06:44:39:2b (Reason: 1)
Aug 21 10:25:39 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-DISCONNECTED bssid=20:37:06:44:39:2b reason=1
Aug 21 10:25:39 IBMT540p NetworkManager[852]: <warn> Connection disconnected (reason 1)
Aug 21 10:25:39 IBMT540p kernel: [ 1617.964854] cfg80211: Calling CRDA to update world regulatory domain
Aug 21 10:25:39 IBMT540p kernel: [ 1617.967464] cfg80211: World regulatory domain updated:
Aug 21 10:25:39 IBMT540p kernel: [ 1617.967468] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 10:25:39 IBMT540p kernel: [ 1617.967470] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:39 IBMT540p kernel: [ 1617.967471] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:39 IBMT540p kernel: [ 1617.967473] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:39 IBMT540p kernel: [ 1617.967474] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:39 IBMT540p kernel: [ 1617.967475] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:39 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: associated -> disconnected
Aug 21 10:25:39 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 21 10:25:39 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 21 10:25:39 IBMT540p wpa_supplicant[982]: wlan0: SME: Trying to authenticate with 1c:aa:07:43:6e:e4 (SSID='ATEA' freq=2412 MHz)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.334748] wlan0: authenticate with 1c:aa:07:43:6e:e4
Aug 21 10:25:39 IBMT540p wpa_supplicant[982]: wlan0: Trying to associate with 1c:aa:07:43:6e:e4 (SSID='ATEA' freq=2412 MHz)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.336521] wlan0: send auth to 1c:aa:07:43:6e:e4 (try 1/3)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.338169] wlan0: authenticated
Aug 21 10:25:39 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: scanning -> associating
Aug 21 10:25:39 IBMT540p wpa_supplicant[982]: wlan0: Associated with 1c:aa:07:43:6e:e4
Aug 21 10:25:39 IBMT540p kernel: [ 1618.340198] wlan0: associate with 1c:aa:07:43:6e:e4 (try 1/3)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.342160] wlan0: RX AssocResp from 1c:aa:07:43:6e:e4 (capab=0x431 status=0 aid=4)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.343207] wlan0: associated
Aug 21 10:25:39 IBMT540p kernel: [ 1618.343272] cfg80211: Calling CRDA for country: NO
Aug 21 10:25:39 IBMT540p kernel: [ 1618.345914] cfg80211: Regulatory domain changed to country: NO
Aug 21 10:25:39 IBMT540p kernel: [ 1618.345919] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.345921] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.345923] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.345924] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.345925] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Aug 21 10:25:39 IBMT540p kernel: [ 1618.345927] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Aug 21 10:25:39 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: associating -> associated
Aug 21 10:25:40 IBMT540p kernel: [ 1619.345653] wlan0: deauthenticated from 1c:aa:07:43:6e:e4 (Reason: 7)
Aug 21 10:25:40 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-DISCONNECTED bssid=1c:aa:07:43:6e:e4 reason=7
Aug 21 10:25:40 IBMT540p NetworkManager[852]: <warn> Connection disconnected (reason 7)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.354584] cfg80211: Calling CRDA to update world regulatory domain
Aug 21 10:25:40 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: associated -> disconnected
Aug 21 10:25:40 IBMT540p kernel: [ 1619.358083] cfg80211: World regulatory domain updated:
Aug 21 10:25:40 IBMT540p kernel: [ 1619.358089] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.358092] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.358095] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.358098] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.358101] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.358104] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:40 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 21 10:25:40 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 21 10:25:40 IBMT540p wpa_supplicant[982]: wlan0: SME: Trying to authenticate with 1c:aa:07:6e:47:0b (SSID='ATEA' freq=5180 MHz)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.638643] wlan0: authenticate with 1c:aa:07:6e:47:0b
Aug 21 10:25:40 IBMT540p kernel: [ 1619.640691] wlan0: send auth to 1c:aa:07:6e:47:0b (try 1/3)
Aug 21 10:25:40 IBMT540p wpa_supplicant[982]: wlan0: Trying to associate with 1c:aa:07:6e:47:0b (SSID='ATEA' freq=5180 MHz)
Aug 21 10:25:40 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: scanning -> associating
Aug 21 10:25:40 IBMT540p kernel: [ 1619.641289] wlan0: authenticated
Aug 21 10:25:40 IBMT540p kernel: [ 1619.645230] wlan0: associate with 1c:aa:07:6e:47:0b (try 1/3)
Aug 21 10:25:40 IBMT540p wpa_supplicant[982]: wlan0: Associated with 1c:aa:07:6e:47:0b
Aug 21 10:25:40 IBMT540p kernel: [ 1619.646179] wlan0: RX AssocResp from 1c:aa:07:6e:47:0b (capab=0x111 status=0 aid=3)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.647095] wlan0: associated
Aug 21 10:25:40 IBMT540p kernel: [ 1619.647140] cfg80211: Calling CRDA for country: NO
Aug 21 10:25:40 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: associating -> associated
Aug 21 10:25:40 IBMT540p kernel: [ 1619.649463] cfg80211: Regulatory domain changed to country: NO
Aug 21 10:25:40 IBMT540p kernel: [ 1619.649467] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.649470] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.649471] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.649473] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.649475] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Aug 21 10:25:40 IBMT540p kernel: [ 1619.649476] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Aug 21 10:25:45 IBMT540p kernel: [ 1624.613768] wlan0: deauthenticated from 1c:aa:07:6e:47:0b (Reason: 3)
Aug 21 10:25:45 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-DISCONNECTED bssid=1c:aa:07:6e:47:0b reason=3
Aug 21 10:25:45 IBMT540p NetworkManager[852]: <warn> Connection disconnected (reason 3)
Aug 21 10:25:45 IBMT540p kernel: [ 1624.622835] cfg80211: Calling CRDA to update world regulatory domain
Aug 21 10:25:45 IBMT540p kernel: [ 1624.625167] cfg80211: World regulatory domain updated:
Aug 21 10:25:45 IBMT540p kernel: [ 1624.625169] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 10:25:45 IBMT540p kernel: [ 1624.625170] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:45 IBMT540p kernel: [ 1624.625171] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:45 IBMT540p kernel: [ 1624.625172] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:45 IBMT540p kernel: [ 1624.625173] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:45 IBMT540p kernel: [ 1624.625173] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:45 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: associated -> disconnected
Aug 21 10:25:45 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 21 10:25:45 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 21 10:25:46 IBMT540p wpa_supplicant[982]: wlan0: SME: Trying to authenticate with 1c:aa:07:43:71:db (SSID='ATEA' freq=5300 MHz)
Aug 21 10:25:46 IBMT540p kernel: [ 1624.944369] wlan0: authenticate with 1c:aa:07:43:71:db
Aug 21 10:25:46 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 21 10:25:46 IBMT540p kernel: [ 1624.946402] wlan0: direct probe to 1c:aa:07:43:71:db (try 1/3)
Aug 21 10:25:46 IBMT540p kernel: [ 1625.150649] wlan0: direct probe to 1c:aa:07:43:71:db (try 2/3)
Aug 21 10:25:46 IBMT540p kernel: [ 1625.354639] wlan0: direct probe to 1c:aa:07:43:71:db (try 3/3)
Aug 21 10:25:46 IBMT540p kernel: [ 1625.557999] wlan0: authentication with 1c:aa:07:43:71:db timed out
Aug 21 10:25:46 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 21 10:25:46 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 21 10:25:46 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 21 10:25:46 IBMT540p wpa_supplicant[982]: wlan0: SME: Trying to authenticate with 1c:aa:07:43:6e:eb (SSID='ATEA' freq=5660 MHz)
Aug 21 10:25:46 IBMT540p kernel: [ 1625.701243] wlan0: authenticate with 1c:aa:07:43:6e:eb
Aug 21 10:25:46 IBMT540p kernel: [ 1625.703370] wlan0: direct probe to 1c:aa:07:43:6e:eb (try 1/3)
Aug 21 10:25:46 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 21 10:25:46 IBMT540p kernel: [ 1625.907092] wlan0: direct probe to 1c:aa:07:43:6e:eb (try 2/3)
Aug 21 10:25:47 IBMT540p kernel: [ 1626.111268] wlan0: direct probe to 1c:aa:07:43:6e:eb (try 3/3)
Aug 21 10:25:47 IBMT540p kernel: [ 1626.314595] wlan0: authentication with 1c:aa:07:43:6e:eb timed out
Aug 21 10:25:47 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 21 10:25:47 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 21 10:25:47 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 21 10:25:51 IBMT540p wpa_supplicant[982]: wlan0: SME: Trying to authenticate with 1c:aa:07:6e:47:04 (SSID='ATEA' freq=2462 MHz)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.003911] wlan0: authenticate with 1c:aa:07:6e:47:04
Aug 21 10:25:51 IBMT540p kernel: [ 1630.005701] wlan0: direct probe to 1c:aa:07:6e:47:04 (try 1/3)
Aug 21 10:25:51 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 21 10:25:51 IBMT540p kernel: [ 1630.210706] wlan0: direct probe to 1c:aa:07:6e:47:04 (try 2/3)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.415668] wlan0: direct probe to 1c:aa:07:6e:47:04 (try 3/3)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.618065] wlan0: authentication with 1c:aa:07:6e:47:04 timed out
Aug 21 10:25:51 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 21 10:25:51 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 21 10:25:51 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 21 10:25:51 IBMT540p wpa_supplicant[982]: wlan0: SME: Trying to authenticate with 1c:aa:07:7b:17:64 (SSID='ATEA' freq=2462 MHz)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.769156] wlan0: authenticate with 1c:aa:07:7b:17:64
Aug 21 10:25:51 IBMT540p kernel: [ 1630.770860] wlan0: send auth to 1c:aa:07:7b:17:64 (try 1/3)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.773656] wlan0: authenticated
Aug 21 10:25:51 IBMT540p wpa_supplicant[982]: wlan0: Trying to associate with 1c:aa:07:7b:17:64 (SSID='ATEA' freq=2462 MHz)
Aug 21 10:25:51 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: scanning -> associating
Aug 21 10:25:51 IBMT540p kernel: [ 1630.775161] wlan0: associate with 1c:aa:07:7b:17:64 (try 1/3)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.778179] wlan0: RX AssocResp from 1c:aa:07:7b:17:64 (capab=0x431 status=0 aid=6)
Aug 21 10:25:51 IBMT540p wpa_supplicant[982]: wlan0: Associated with 1c:aa:07:7b:17:64
Aug 21 10:25:51 IBMT540p kernel: [ 1630.779189] wlan0: associated
Aug 21 10:25:51 IBMT540p kernel: [ 1630.779252] cfg80211: Calling CRDA for country: NO
Aug 21 10:25:51 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: associating -> associated
Aug 21 10:25:51 IBMT540p kernel: [ 1630.782474] cfg80211: Regulatory domain changed to country: NO
Aug 21 10:25:51 IBMT540p kernel: [ 1630.782479] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.782480] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.782482] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.782482] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.782483] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Aug 21 10:25:51 IBMT540p kernel: [ 1630.782484] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Aug 21 10:25:52 IBMT540p kernel: [ 1631.363460] wlan0: deauthenticated from 1c:aa:07:7b:17:64 (Reason: 7)
Aug 21 10:25:52 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-DISCONNECTED bssid=1c:aa:07:7b:17:64 reason=7
Aug 21 10:25:52 IBMT540p NetworkManager[852]: <warn> Connection disconnected (reason 7)
Aug 21 10:25:52 IBMT540p kernel: [ 1631.372102] cfg80211: Calling CRDA to update world regulatory domain
Aug 21 10:25:52 IBMT540p kernel: [ 1631.374081] cfg80211: World regulatory domain updated:
Aug 21 10:25:52 IBMT540p kernel: [ 1631.374083] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 10:25:52 IBMT540p kernel: [ 1631.374085] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:52 IBMT540p kernel: [ 1631.374086] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:52 IBMT540p kernel: [ 1631.374087] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:52 IBMT540p kernel: [ 1631.374088] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:52 IBMT540p kernel: [ 1631.374089] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 10:25:52 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: associated -> disconnected
Aug 21 10:25:52 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 21 10:25:52 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 21 10:25:56 IBMT540p wpa_supplicant[982]: wlan0: SME: Trying to authenticate with 1c:aa:07:43:71:d4 (SSID='ATEA' freq=2412 MHz)
Aug 21 10:25:56 IBMT540p kernel: [ 1635.056771] wlan0: authenticate with 1c:aa:07:43:71:d4
Aug 21 10:25:56 IBMT540p kernel: [ 1635.058626] wlan0: direct probe to 1c:aa:07:43:71:d4 (try 1/3)
Aug 21 10:25:56 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 21 10:25:56 IBMT540p kernel: [ 1635.262426] wlan0: direct probe to 1c:aa:07:43:71:d4 (try 2/3)
Aug 21 10:25:56 IBMT540p kernel: [ 1635.466565] wlan0: direct probe to 1c:aa:07:43:71:d4 (try 3/3)
Aug 21 10:25:56 IBMT540p kernel: [ 1635.670192] wlan0: authentication with 1c:aa:07:43:71:d4 timed out
Aug 21 10:25:56 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 21 10:25:56 IBMT540p wpa_supplicant[982]: wlan0: CTRL-EVENT-SCAN-STARTED 
Aug 21 10:25:56 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 21 10:25:59 IBMT540p NetworkManager[852]: <warn> Activation (wlan0/wireless): association took too long.
Aug 21 10:25:59 IBMT540p NetworkManager[852]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Aug 21 10:25:59 IBMT540p NetworkManager[852]: <warn> Activation (wlan0/wireless): asking for new secrets
Aug 21 10:25:59 IBMT540p NetworkManager[852]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 21 10:25:59 IBMT540p dbus[736]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Aug 21 10:25:59 IBMT540p dbus[736]: [system] Successfully activated service 'org.freedesktop.hostname1'
Aug 21 10:25:59 IBMT540p NetworkManager[852]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 21 10:26:00 IBMT540p NetworkManager[852]: <info> (wlan0): supplicant interface state: scanning -> inactive
Aug 21 10:26:03 IBMT540p NetworkManager[852]: <warn> No agents were available for this request.
Aug 21 10:26:03 IBMT540p NetworkManager[852]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Aug 21 10:26:03 IBMT540p NetworkManager[852]: <info> NetworkManager state is now DISCONNECTED
Aug 21 10:26:03 IBMT540p NetworkManager[852]: <info> Marking connection 'ATEA' invalid.
Aug 21 10:26:03 IBMT540p NetworkManager[852]: <warn> Activation (wlan0) failed for connection 'ATEA'
Aug 21 10:26:03 IBMT540p NetworkManager[852]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 21 10:26:03 IBMT540p NetworkManager[852]: <info> (wlan0): deactivating device (reason 'none') [0]

```

I'm unable to fint out whats wrong. I need help..


Geir.

---

### Post by Geir_Klamas on 2014-08-28
An update: 

It appears that PEAP is not the problem. I purchase a [Asus N10 nano]("http://www.asus.com/Networking/USBN10_NANO/"), and set it up with PEAP. Everything worked just fine. I'll take a closer look at the drivers of the internal intel card.

Geir

---

### Post by boulayj on 2014-09-22
I got the same issue with my Thinkpad T540p.
 It seems to be solved since I've flashed the bios with the latest version available on lenovo's support pages : [http://support.lenovo.com/us/en/downloads/ds038147](http://support.lenovo.com/us/en/downloads/ds038147).

Julien

---

### Post by boulayj on 2014-09-24
I finaly manage to solve the issue by installing the latest kernel version 3.17RC6.

 My ethernet connection was not working too, so I opened new bugs on launchpad. Here are the links for these 2 bugs :
- [[Lenovo ThinkPad T540p] Wifi disconnecting every 2 minutes with Intel Wireless 7260AC]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372033")
- [Unable to connect to ethernet with Intel I217-LM]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1373276")

To update your kernel to the latest version, follow the guidelines provided on the [wiki]("https://wiki.ubuntu.com/Kernel/MainlineBuilds?action=show&redirect=KernelMainlineBuilds")

Hope this can help !

---

### Post by Geir_Klamas on 2015-02-19
Hi.
I have flashed the bios on my laptop, and it did not fix the problem. Using the 3.17rc6 kernel did not work for me. I have the same problem with this kernel. I also installed the 3.19rc7 kernel and no change.

Geir

---

