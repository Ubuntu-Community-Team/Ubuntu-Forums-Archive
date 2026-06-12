---
title: "Wireless WPA2 Enterprise"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Vaeil on 2008-09-03
Hey there,

I have an Acer Aspire 6920. Wireless works fine on the system, with any basic encryption I tried (WEP, WPA), just click the network and go. Wired networking went great after installing the drivers from Acer. My university however uses a Dynamic WEP on WPA2 Enterprise, which doesn't function at all.

Attempting to connect through the "Connect to other wireless network" dialog, I get a list of errors (Errors at the end of the post.). I have followed both ways the university provides per helpdesk, namely this one: [http://www.snt.utwente.nl/handleidingen/1/44](http://www.snt.utwente.nl/handleidingen/1/44) (Select English in the top right), and this one via command line: [http://www.snt.utwente.nl/handleidingen/1/60](http://www.snt.utwente.nl/handleidingen/1/60) . Neither of which had any effect. lsmod identifies it as an iwl4963 card (more specifically: iwlwifi_mac80211      219108  1 iwl4965)

The syslog displays a stream of this block of errors when starting up the network in an environment where the WLAN is available:

Sep  3 10:18:09 Alyssa NetworkManager: <info>  Wireless now enabled by radio killswitch 
Sep  3 10:18:12 Alyssa kernel: [  997.772195] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  3 10:18:14 Alyssa kernel: [  998.288010] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:18:25 Alyssa kernel: [  998.686831] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:18:54 Alyssa kernel: [ 1001.742686] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:19:24 Alyssa kernel: [ 1011.013735] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate

And the following error when attempting to connect after configuration. Which repeats for about a minute as it tries to connect:

Sep  3 10:28:07 Alyssa dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Sep  3 10:28:07 Alyssa NetworkManager: <debug> [1220430487.561285] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'WLAN' 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / WLAN 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  Deactivating device wlan0. 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  Device wlan0 activation scheduled... 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  Activation (wlan0) started... 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Sep  3 10:28:07 Alyssa NetworkManager: <info>  Activation (wlan0/wireless): access point 'WLAN' is encrypted, and a key exists.  No new key needed. 
Sep  3 10:28:08 Alyssa NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Sep  3 10:28:08 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was '0' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 574c414e' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt IEEE8021X' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 phase2 "auth=PAP"' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 eap TTLS' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 identity "hiddenusername@utwente.nl"' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 password <password>' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 anonymous_identity "hiddenusername@utwente.nl"' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ca_cert "/usr/share/ca-certificates/surfnet.pem"' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 fragment_size 1300' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Sep  3 10:28:09 Alyssa NetworkManager: <debug> [1220430489.115040] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:18:74:D6:ED:30 to 00:11:20:EE:63:DF on wireless network 'WLAN' 
Sep  3 10:28:09 Alyssa NetworkManager: <debug> [1220430489.117602] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'WLAN' 
Sep  3 10:28:09 Alyssa NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Sep  3 10:28:11 Alyssa kernel: [ 1084.554925] wlan0: Initial auth_alg=0
Sep  3 10:28:11 Alyssa kernel: [ 1084.554933] wlan0: authenticate with AP 00:11:20:ee:63:df
Sep  3 10:28:11 Alyssa kernel: [ 1084.554952] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:28:11 Alyssa kernel: [ 1084.557753] wlan0: Initial auth_alg=0
Sep  3 10:28:11 Alyssa kernel: [ 1084.557759] wlan0: authenticate with AP 00:11:20:ee:63:df
Sep  3 10:28:11 Alyssa kernel: [ 1084.557770] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:28:11 Alyssa kernel: [ 1084.566173] wlan0: Initial auth_alg=0
Sep  3 10:28:11 Alyssa kernel: [ 1084.566179] wlan0: authenticate with AP 00:18:74:d6:ed:30
Sep  3 10:28:11 Alyssa kernel: [ 1084.566190] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:28:11 Alyssa kernel: [ 1084.567544] wlan0: Initial auth_alg=0
Sep  3 10:28:11 Alyssa kernel: [ 1084.567550] wlan0: authenticate with AP 00:18:74:d6:ed:30
Sep  3 10:28:11 Alyssa kernel: [ 1084.567560] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:28:11 Alyssa kernel: [ 1084.629113] wlan0: authenticate with AP 00:18:74:d6:ed:30
Sep  3 10:28:11 Alyssa kernel: [ 1084.629129] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:28:11 Alyssa kernel: [ 1084.694599] wlan0: authenticate with AP 00:18:74:d6:ed:30
Sep  3 10:28:11 Alyssa kernel: [ 1084.694615] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:28:11 Alyssa kernel: [ 1084.748264] wlan0: authentication with AP 00:18:74:d6:ed:30 timed out
Sep  3 10:28:11 Alyssa kernel: [ 1084.748270] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 10:28:13 Alyssa NetworkManager: <debug> [1220430493.116153] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:11:20:EE:63:DF to 00:18:74:D6:ED:30 on wireless network 'WLAN' 
Sep  3 10:28:13 Alyssa NetworkManager: <debug> [1220430493.118145] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'WLAN' 
Sep  3 10:28:13 Alyssa NetworkManager: <info>  Old device 'wlan0' activating, won't change. 

Please keep in mind that I most probably can't connect to the internet on the campus unless I can ask teh network guys with puppy eyes, so if anyone has an idea on a way to fix this beforehand, or without using the internet, I'd be most grateful. If I have to use the internet, well, I'd still be very grateful.

---

