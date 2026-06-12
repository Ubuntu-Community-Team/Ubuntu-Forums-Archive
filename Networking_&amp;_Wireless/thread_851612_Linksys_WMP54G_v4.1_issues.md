---
title: "Linksys WMP54G v4.1 issues"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by ykmo on 2008-07-06
I've got a Linksys WMP54G PCI card inside of my box. It works fine with my network on windows. It works fine with the neighbor's unsecured network. Attached is a log of what happens when I try to connect with the correct credentials to my network.

```
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Device wlan0 activation scheduled... 
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Activation (wlan0) started... 
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'ADIO' is encrypted, but NO valid key exists.  New key needed. 
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'ADIO'. 
Jul  7 00:35:24 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jul  7 00:35:40 ubuntu kernel: [ 1298.161398] wlan0: No ProbeResp from current AP 00:18:f8:72:62:e1 - assume out of range
Jul  7 00:35:45 ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'ADIO' received. 
Jul  7 00:35:45 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul  7 00:35:45 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jul  7 00:35:45 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jul  7 00:35:45 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jul  7 00:35:45 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jul  7 00:35:45 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'ADIO' is encrypted, and a key exists.  No new key needed. 
Jul  7 00:35:46 ubuntu NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: response was '0' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4144494f' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Jul  7 00:35:47 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jul  7 00:35:48 ubuntu kernel: [ 1305.346978] wlan0: Initial auth_alg=0
Jul  7 00:35:48 ubuntu kernel: [ 1305.346983] wlan0: authenticate with AP 00:12:88:33:2a:e9
Jul  7 00:35:48 ubuntu kernel: [ 1305.348252] wlan0: RX authentication from 00:12:88:33:2a:e9 (alg=0 transaction=2 status=0)
Jul  7 00:35:48 ubuntu kernel: [ 1305.348255] wlan0: authenticated
Jul  7 00:35:48 ubuntu kernel: [ 1305.348258] wlan0: associate with AP 00:12:88:33:2a:e9
Jul  7 00:35:48 ubuntu kernel: [ 1305.546512] wlan0: associate with AP 00:12:88:33:2a:e9
Jul  7 00:35:48 ubuntu kernel: [ 1305.746111] wlan0: associate with AP 00:12:88:33:2a:e9
Jul  7 00:35:48 ubuntu kernel: [ 1305.945708] wlan0: association with AP 00:12:88:33:2a:e9 timed out
Jul  7 00:35:53 ubuntu NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul  7 00:36:26 ubuntu last message repeated 5 times
Jul  7 00:36:32 ubuntu NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul  7 00:36:33 ubuntu kernel: [ 1350.468125] wlan0: Initial auth_alg=0
Jul  7 00:36:33 ubuntu kernel: [ 1350.468130] wlan0: authenticate with AP 00:12:88:33:2a:e9
Jul  7 00:36:33 ubuntu kernel: [ 1350.468670] wlan0: Initial auth_alg=0
Jul  7 00:36:33 ubuntu kernel: [ 1350.468673] wlan0: authenticate with AP 00:12:88:33:2a:e9
Jul  7 00:36:33 ubuntu kernel: [ 1350.469598] wlan0: RX authentication from 00:12:88:33:2a:e9 (alg=0 transaction=2 status=0)
Jul  7 00:36:33 ubuntu kernel: [ 1350.469601] wlan0: authenticated
Jul  7 00:36:33 ubuntu kernel: [ 1350.469603] wlan0: associate with AP 00:12:88:33:2a:e9
Jul  7 00:36:33 ubuntu kernel: [ 1350.472482] wlan0: authentication frame received from 00:12:88:33:2a:e9, but not in authenticate state - ignored
Jul  7 00:36:33 ubuntu kernel: [ 1350.667582] wlan0: associate with AP 00:12:88:33:2a:e9
Jul  7 00:36:33 ubuntu kernel: [ 1350.867180] wlan0: associate with AP 00:12:88:33:2a:e9
Jul  7 00:36:33 ubuntu kernel: [ 1351.066777] wlan0: association with AP 00:12:88:33:2a:e9 timed out
Jul  7 00:36:38 ubuntu NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Jul  7 00:36:47 ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), asking for new key. 
Jul  7 00:36:47 ubuntu NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'ADIO'. 

```

I'm not sure where the problem is, exactly. I do know that the router is pretty old and could use replacing, but all of the other computers in the house work fine with it. (It's a 2WIRE HomePortal 1700HW DSL Modem/Router combo box from my ISP)

I did see the [Wiki article]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys") about Linksys cards but I wasn't sure if the article for v4.1 has been updated for 8.04 or not.

---

