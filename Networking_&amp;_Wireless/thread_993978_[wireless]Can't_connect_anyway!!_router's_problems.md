---
title: "[wireless]Can't connect anyway!! router's problems?"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by eskimo on 2008-11-26
Hi to you all, my configuration is:
HP Pavilion 6870 with Intel Corporation PRO/Wireless 4965 AG that perfectly works with lots of routers. I have Ubuntu Hardy Heron and i use network manager.


I've changed house and as well internet connection, here i have an ADSL router (i don't know which, is that came with the adsl contract) and here i can't connect with wireless! I can only use the cable to go to internet, as well my friends here in the house with windows xp. Only a girl with a windows vista could.

I try to connect with WPA, WEP, without security but i can't use the wireless anyway. Ideas? Here i post my syslog output:


> Nov 26 15:20:49 eskimo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Nov 26 15:20:49 eskimo-laptop NetworkManager: <debug> [1227709249.109956] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Livebox-7638' 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / Livebox-7638 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Deactivating device wlan0. 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Activation (wlan0) started... 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Livebox-7638' is encrypted, but NO valid key exists.  New key needed. 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Livebox-7638'. 
Nov 26 15:20:49 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 

this is the output before inserting the key (wpa)

> Nov 26 15:21:24 eskimo-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'Livebox-7638' received. 
Nov 26 15:21:24 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 26 15:21:24 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 26 15:21:24 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 26 15:21:24 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 26 15:21:24 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 26 15:21:24 eskimo-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'Livebox-7638' is encrypted, and a key exists.  No new key needed. 
Nov 26 15:21:25 eskimo-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Nov 26 15:21:25 eskimo-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Nov 26 15:21:26 eskimo-laptop kernel: [  142.091895] NET: Registered protocol family 17
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: response was '0' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4c697665626f782d37363338' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  SUP: response was 'OK' 
Nov 26 15:21:26 eskimo-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 26 15:21:28 eskimo-laptop kernel: [  144.447893] wlan0: Initial auth_alg=0
Nov 26 15:21:28 eskimo-laptop kernel: [  144.447897] wlan0: authenticate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:28 eskimo-laptop kernel: [  144.450042] wlan0: RX authentication from 00:1f:3a:3f:89:c0 (alg=0 transaction=2 status=0)
Nov 26 15:21:28 eskimo-laptop kernel: [  144.450045] wlan0: authenticated
Nov 26 15:21:28 eskimo-laptop kernel: [  144.450046] wlan0: associate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:28 eskimo-laptop kernel: [  144.454030] wlan0: invalid aid value 0; bits 15:14 not set
Nov 26 15:21:28 eskimo-laptop kernel: [  144.454033] wlan0: RX AssocResp from 00:1f:3a:3f:89:c0 (capab=0x411 status=1 aid=0)
Nov 26 15:21:28 eskimo-laptop kernel: [  144.454035] wlan0: AP denied association (code=1)
Nov 26 15:21:28 eskimo-laptop kernel: [  144.649308] wlan0: associate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:28 eskimo-laptop kernel: [  144.669283] wlan0: invalid aid value 0; bits 15:14 not set
Nov 26 15:21:28 eskimo-laptop kernel: [  144.669289] wlan0: RX AssocResp from 00:1f:3a:3f:89:c0 (capab=0x411 status=1 aid=0)
Nov 26 15:21:28 eskimo-laptop kernel: [  144.669290] wlan0: AP denied association (code=1)
Nov 26 15:21:28 eskimo-laptop kernel: [  144.849015] wlan0: associate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:28 eskimo-laptop kernel: [  144.851732] wlan0: invalid aid value 0; bits 15:14 not set
Nov 26 15:21:28 eskimo-laptop kernel: [  144.851739] wlan0: RX AssocResp from 00:1f:3a:3f:89:c0 (capab=0x411 status=1 aid=0)
Nov 26 15:21:28 eskimo-laptop kernel: [  144.851742] wlan0: AP denied association (code=1)
Nov 26 15:21:28 eskimo-laptop kernel: [  145.048714] wlan0: association with AP 00:1f:3a:3f:89:c0 timed out
Nov 26 15:21:33 eskimo-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Nov 26 15:21:40 eskimo-laptop kernel: [  156.535287] wlan0: Initial auth_alg=0
Nov 26 15:21:40 eskimo-laptop kernel: [  156.535298] wlan0: authenticate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:40 eskimo-laptop kernel: [  156.537401] wlan0: RX authentication from 00:1f:3a:3f:89:c0 (alg=0 transaction=2 status=0)
Nov 26 15:21:40 eskimo-laptop kernel: [  156.537409] wlan0: authenticated
Nov 26 15:21:40 eskimo-laptop kernel: [  156.537414] wlan0: associate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:40 eskimo-laptop kernel: [  156.538285] wlan0: authentication frame received from 00:1f:3a:3f:89:c0, but not in authenticate state - ignored
Nov 26 15:21:40 eskimo-laptop kernel: [  156.543088] wlan0: Initial auth_alg=0
Nov 26 15:21:40 eskimo-laptop kernel: [  156.543102] wlan0: authenticate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:40 eskimo-laptop kernel: [  156.543137] wlan0: association frame received from 00:1f:3a:3f:89:c0, but not in associate state - ignored
Nov 26 15:21:40 eskimo-laptop kernel: [  156.546781] wlan0: association frame received from 00:1f:3a:3f:89:c0, but not in associate state - ignored
Nov 26 15:21:40 eskimo-laptop kernel: [  156.547585] wlan0: RX authentication from 00:1f:3a:3f:89:c0 (alg=0 transaction=2 status=0)
Nov 26 15:21:40 eskimo-laptop kernel: [  156.547592] wlan0: authenticated
Nov 26 15:21:40 eskimo-laptop kernel: [  156.547596] wlan0: associate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:40 eskimo-laptop kernel: [  156.550393] wlan0: invalid aid value 0; bits 15:14 not set
Nov 26 15:21:40 eskimo-laptop kernel: [  156.550402] wlan0: RX AssocResp from 00:1f:3a:3f:89:c0 (capab=0x411 status=1 aid=0)
Nov 26 15:21:40 eskimo-laptop kernel: [  156.550406] wlan0: AP denied association (code=1)
Nov 26 15:21:40 eskimo-laptop kernel: [  156.743585] wlan0: associate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:40 eskimo-laptop kernel: [  156.746301] wlan0: invalid aid value 0; bits 15:14 not set
Nov 26 15:21:40 eskimo-laptop kernel: [  156.746314] wlan0: RX AssocResp from 00:1f:3a:3f:89:c0 (capab=0x411 status=1 aid=0)
Nov 26 15:21:40 eskimo-laptop kernel: [  156.746319] wlan0: AP denied association (code=1)
Nov 26 15:21:40 eskimo-laptop kernel: [  156.943260] wlan0: associate with AP 00:1f:3a:3f:89:c0
Nov 26 15:21:40 eskimo-laptop kernel: [  156.945974] wlan0: invalid aid value 0; bits 15:14 not set
Nov 26 15:21:40 eskimo-laptop kernel: [  156.945987] wlan0: RX AssocResp from 00:1f:3a:3f:89:c0 (capab=0x411 status=1 aid=0)
Nov 26 15:21:40 eskimo-laptop kernel: [  156.945991] wlan0: AP denied association (code=1)
Nov 26 15:21:41 eskimo-laptop kernel: [  157.143028] wlan0: association with AP 00:1f:3a:3f:89:c0 timed out
Nov 26 15:21:45 eskimo-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change.

and this when i insert the key and it try to connect...

---

