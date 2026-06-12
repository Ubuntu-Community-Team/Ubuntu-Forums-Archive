---
title: "Intel Wireless 3945 problems"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Nalroff on 2008-09-07
I have a Toshiba Satellite A-105 and a WD Portable hard drive from which I run Ubuntu 8.04. Using Network Manager, I have successfully connected to two home wireless networks using WPA security keys. No hitch, just type code and go -- beautiful.

On campus, however, I have a different story. The campus wireless is setup as an 802.1x WEP, PEAP, MS-CHAPv2 network. This creates an annoyance, but apparently not for everyone. Being in the Computer Science department, there's bound to be another Linux nerd like myself, right? Well, I found one, and he also runs Hardy. He sets up his Network Manager to authenticate via LEAP and 802.1x just like the MacBooks do. I set mine up this way and to no avail. It tries to connect for about 3 minutes and then times out. I ran across a recurring set of messages on Syslog, and if someone can decipher them, then God bless you. Here they are:

> Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>120s), failing activation. 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Sep  3 14:13:55 andy-laptop NetworkManager: <debug> [1220465635.381290] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:13:5F:FA:19:A0 to 00:13:5F:FA:36:60 on wireless network 'ETSU' 
Sep  3 14:13:55 andy-laptop NetworkManager: <debug> [1220465635.383907] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ETSU' 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  SWITCH: found better connection 'wlan0/ETSU' than current connection 'wlan0/ETSU'.  same_ssid=1, have_link=0 
Sep  3 14:13:55 andy-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Will activate connection 'wlan0/ETSU'. 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Deactivating device wlan0. 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0) started... 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (ETSU) 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0) failed. 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Deactivating device wlan0. 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0): cancelling... 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0) cancellation handler scheduled... 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0): waiting for device to cancel activation. 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0) cancellation handled. 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Sep  3 14:13:55 andy-laptop NetworkManager: <info>  Activation (wlan0): cancelled. 
Sep  3 14:14:20 andy-laptop kernel: [  481.089027] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:14:50 andy-laptop kernel: [  511.090501] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:14:50 andy-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Sep  3 14:14:50 andy-laptop NetworkManager: <debug> [1220465690.766450] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'ETSU' 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / ETSU 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Deactivating device wlan0. 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) started... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'ETSU' is encrypted, but NO valid key exists.  New key needed. 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'ETSU'. 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'ETSU' received. 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Sep  3 14:14:50 andy-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'ETSU' is encrypted, and a key exists.  No new key needed. 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was '0' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 45545355' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt IEEE8021X' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 eap LEAP' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 identity "?my username?"' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 password <password>' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep  3 14:14:52 andy-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Sep  3 14:14:54 andy-laptop kernel: [  514.778021] wlan0: Initial auth_alg=128
Sep  3 14:14:54 andy-laptop kernel: [  514.778033] wlan0: authenticate with AP 00:13:5f:fa:36:60
Sep  3 14:14:54 andy-laptop kernel: [  514.778062] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:14:54 andy-laptop kernel: [  514.778826] wlan0: Initial auth_alg=128
Sep  3 14:14:54 andy-laptop kernel: [  514.778834] wlan0: authenticate with AP 00:13:5f:fa:36:60
Sep  3 14:14:54 andy-laptop kernel: [  514.778858] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:14:54 andy-laptop kernel: [  514.781861] wlan0: Initial auth_alg=128
Sep  3 14:14:54 andy-laptop kernel: [  514.781870] wlan0: authenticate with AP 00:13:5f:fa:19:a0
Sep  3 14:14:54 andy-laptop kernel: [  514.781887] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:14:54 andy-laptop kernel: [  514.783219] wlan0: Initial auth_alg=128
Sep  3 14:14:54 andy-laptop kernel: [  514.783228] wlan0: authenticate with AP 00:13:5f:fa:19:a0
Sep  3 14:14:54 andy-laptop kernel: [  514.783242] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:14:54 andy-laptop kernel: [  514.783258] wlan0: RX authentication from 00:13:5f:fa:19:a0 (alg=128 transaction=2 status=0)
Sep  3 14:14:54 andy-laptop kernel: [  514.783264] wlan0: authenticated
Sep  3 14:14:54 andy-laptop kernel: [  514.783271] wlan0: associate with AP 00:13:5f:fa:19:a0
Sep  3 14:14:54 andy-laptop kernel: [  514.783278] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
Sep  3 14:14:54 andy-laptop kernel: [  514.787624] wlan0: authentication frame received from 00:13:5f:fa:19:a0, but not in authenticate state - ignored
Sep  3 14:14:54 andy-laptop kernel: [  514.983359] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:14:54 andy-laptop NetworkManager: <debug> [1220465694.397265] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:13:5F:FA:36:60 to 00:13:5F:FA:19:A0 on wireless network 'ETSU' 
Sep  3 14:14:54 andy-laptop NetworkManager: <debug> [1220465694.400116] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ETSU' 
Sep  3 14:14:54 andy-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Sep  3 14:14:58 andy-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Sep  3 14:15:05 andy-laptop kernel: [  526.456532] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:15:05 andy-laptop kernel: [  526.458109] wlan0: Initial auth_alg=128
Sep  3 14:15:05 andy-laptop kernel: [  526.458119] wlan0: authenticate with AP 00:13:5f:fa:19:a0
Sep  3 14:15:05 andy-laptop kernel: [  526.458139] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:15:05 andy-laptop kernel: [  526.460069] wlan0: Initial auth_alg=128
Sep  3 14:15:05 andy-laptop kernel: [  526.460079] wlan0: authenticate with AP 00:13:5f:fa:19:a0
Sep  3 14:15:05 andy-laptop kernel: [  526.460093] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:15:05 andy-laptop kernel: [  526.460109] wlan0: RX authentication from 00:13:5f:fa:19:a0 (alg=128 transaction=2 status=0)
Sep  3 14:15:05 andy-laptop kernel: [  526.460116] wlan0: authenticated
Sep  3 14:15:05 andy-laptop kernel: [  526.460123] wlan0: associate with AP 00:13:5f:fa:19:a0
Sep  3 14:15:05 andy-laptop kernel: [  526.460129] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
Sep  3 14:15:05 andy-laptop kernel: [  526.463432] wlan0: authentication frame received from 00:13:5f:fa:19:a0, but not in authenticate state - ignored
Sep  3 14:15:05 andy-laptop kernel: [  526.463938] wlan0: authentication frame received from 00:13:5f:fa:19:a0, but not in authenticate state - ignored
Sep  3 14:15:05 andy-laptop kernel: [  526.657150] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:15:10 andy-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Sep  3 14:15:17 andy-laptop kernel: [  538.139643] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:15:17 andy-laptop kernel: [  538.143142] wlan0: Initial auth_alg=128
Sep  3 14:15:17 andy-laptop kernel: [  538.143155] wlan0: authenticate with AP 00:13:5f:fa:19:a0
Sep  3 14:15:17 andy-laptop kernel: [  538.143176] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:15:17 andy-laptop kernel: [  538.144877] wlan0: Initial auth_alg=128
Sep  3 14:15:17 andy-laptop kernel: [  538.144887] wlan0: authenticate with AP 00:13:5f:fa:36:60
Sep  3 14:15:17 andy-laptop kernel: [  538.144902] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:15:17 andy-laptop kernel: [  538.145629] wlan0: Initial auth_alg=128
Sep  3 14:15:17 andy-laptop kernel: [  538.145637] wlan0: authenticate with AP 00:13:5f:fa:36:60
Sep  3 14:15:17 andy-laptop kernel: [  538.145652] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:15:17 andy-laptop kernel: [  538.146718] wlan0: RX authentication from 00:13:5f:fa:36:60 (alg=128 transaction=2 status=0)
Sep  3 14:15:17 andy-laptop kernel: [  538.146725] wlan0: authenticated
Sep  3 14:15:17 andy-laptop kernel: [  538.146732] wlan0: associate with AP 00:13:5f:fa:36:60
Sep  3 14:15:17 andy-laptop kernel: [  538.146738] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
Sep  3 14:15:17 andy-laptop kernel: [  538.148904] wlan0: authentication frame received from 00:13:5f:fa:36:60, but not in authenticate state - ignored
Sep  3 14:15:17 andy-laptop kernel: [  538.343942] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
Sep  3 14:15:18 andy-laptop NetworkManager: <debug> [1220465718.405314] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:13:5F:FA:19:A0 to 00:13:5F:FA:36:60 on wireless network 'ETSU' 
Sep  3 14:15:18 andy-laptop NetworkManager: <debug> [1220465718.408058] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ETSU' 
Sep  3 14:15:18 andy-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Sep  3 14:15:22 andy-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Sep  3 14:15:24 andy-laptop NetworkManager: <debug> [1220465724.405307] nm_device_802_11_wireless_update_bssid(): Roamed from BSSID 00:13:5F:FA:19:A0 to 00:13:5F:FA:36:60 on wireless network 'ETSU' 
Sep  3 14:15:24 andy-laptop NetworkManager: <debug> [1220465724.408231] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ETSU' 
Sep  3 14:15:24 andy-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 

Any help is greatly appreciated.

-Nalroff

---

### Post by carlos.gil on 2008-09-22
I have a similar problem on a dell XPS 1330, have you found a solution?

---

### Post by dimsum_ph on 2008-09-22
this worked for me, try it out.

[http://linuxexpert.wordpress.com/2008/04/28/fix-intel-wireless-driver-on-hardy/]("http://linuxexpert.wordpress.com/2008/04/28/fix-intel-wireless-driver-on-hardy/")

---

### Post by slightly72 on 2008-12-11
It worked for me too, for the iwl4965 module -- thanks for the solution.

---

