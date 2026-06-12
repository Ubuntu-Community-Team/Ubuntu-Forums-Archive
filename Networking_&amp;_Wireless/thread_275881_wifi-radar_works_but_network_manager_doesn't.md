---
title: "wifi-radar works but network manager doesn't"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by Stoph on 2006-10-12
I have gotten my wireless connection to work using wifi-radar, but NetworkManager just doesn't connect.

To fill you in, I'm using a Dell 1500 draft-n wireless card, using ndiswrapper and the windows drivers.

The network doesn't have any encryption or protection.

Here's the entire output from running NetworkManager, because I'm not sure where the problem is:

```
NetworkManager: <information>   Deactivating device eth0.
NetworkManager: <information>   Activation (wlan0) started...
NetworkManager: <information>   Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <information>   match
NetworkManager: <information>   Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <information>   Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <information>   Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <information>   Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <information>   Activation (wlan0/wireless): access point 'lighthouse' is unencrypted, no key needed.
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   SUP: sending command 'INTERFACE_ADD wlan0               ndiswrapper     /var/run/wpa_supplicant      '
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'AP_SCAN 1'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ADD_NETWORK'
NetworkManager: <information>   SUP: response was '0'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 ssid 6c69676874686f757365'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ENABLE_NETWORK 0'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>   wpa_supplicant(32710): Global control interface '/var/run/wpa_supplicant-global'
NetworkManager: <information>   wpa_supplicant(32710): RX global ctrl_iface - hexdump_ascii(len=57):
NetworkManager: <information>   wpa_supplicant(32710):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 77 6c  INTERFACE_ADD wl
NetworkManager: <information>   wpa_supplicant(32710):      61 6e 30 09 09 6e 64 69 73 77 72 61 70 70 65 72  an0__ndiswrapper
NetworkManager: <information>   wpa_supplicant(32710):      09 2f 76 61 72 2f 72 75 6e 2f 77 70 61 5f 73 75  _/var/run/wpa_su
NetworkManager: <information>   wpa_supplicant(32710):      70 70 6c 69 63 61 6e 74 09  pplicant_
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE GLOBAL INTERFACE_ADD 'wlan0           ndiswrapper  /var/run/wpa_supplicant '
NetworkManager: <information>   wpa_supplicant(32710): Initializing interface 'wlan0' conf 'N/A' driver 'ndiswrapper' ctrl_interface '/var/run/wpa_supplicant'
NetworkManager: <information>   wpa_supplicant(32710): Initializing interface (2) 'wlan0'
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: SUPP_PAE entering state DISCONNECTED
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: KEY_RX entering state NO_KEY_RECEIVE
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: SUPP_BE entering state INITIALIZE
NetworkManager: <information>   wpa_supplicant(32710): EAP: EAP entering state DISABLED
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(32710): SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
NetworkManager: <information>   wpa_supplicant(32710):   capabilities: key_mgmt 0xf enc 0xf
NetworkManager: <information>   wpa_supplicant(32710): Own MAC address: 00:16:cf:20:9c:bf
NetworkManager: <information>   wpa_supplicant(32710): Driver does not support WPA.
NetworkManager: <information>   wpa_supplicant(32710): iver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(32710): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(32710): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(32710): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
NetworkManager: <information>   wpa_supplicant(32710): Setting scan request: 0 sec 100000 usec
NetworkManager: <information>   wpa_supplicant(32710): Added interface wlan0
NetworkManager: <information>   wpa_supplicant(32710): Wireless event: cmd=0x8b06 len=8
NetworkManager: <information>   wpa_supplicant(32710): RX ctrl_iface - hexdump_ascii(len=9):
NetworkManager: <information>   wpa_supplicant(32710):      41 50 5f 53 43 41 4e 20 31  AP_SCAN 1
NetworkManager: <information>   wpa_supplicant(32710): RX ctrl_iface - hexdump_ascii(len=11):
NetworkManager: <information>   wpa_supplicant(32710):      41 44 44 5f 4e 45 54 57 4f 52 4b  ADD_NETWORK
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE: ADD_NETWORK
NetworkManager: <information>   wpa_supplicant(32710): RX ctrl_iface - hexdump_ascii(len=39):
NetworkManager: <information>   wpa_supplicant(32710):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73  SET_NETWORK 0 ss
NetworkManager: <information>   wpa_supplicant(32710):      69 64 20 36 63 36 39 36 37 36 38 37 34 36 38 36  id 6c69676874686
NetworkManager: <information>   wpa_supplicant(32710):      66 37 35 37 33 36 35  f757365
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE: SET_NETWORK id=0 name='ssid' value='6c69676874686f757365'
NetworkManager: <information>   wpa_supplicant(32710): ssid - hexdump_ascii(len=10):
NetworkManager: <information>   wpa_supplicant(32710):  lighthouse
NetworkManager: <information>   wpa_supplicant(32710): RX ctrl_iface - hexdump_ascii(len=27):
NetworkManager: <information>   wpa_supplicant(32710):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65  SET_NETWORK 0 ke
NetworkManager: <information>   wpa_supplicant(32710):      79 5f 6d 67 6d 74 20 4e 4f 4e 45  y_mgmt NONE
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' value='NONE'
NetworkManager: <information>   wpa_supplicant(32710): key_mgmt: 0x4
NetworkManager: <information>   wpa_supplicant(32710): RX ctrl_iface - hexdump_ascii(len=16):
NetworkManager: <information>   wpa_supplicant(32710):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30  ENABLE_NETWORK 0
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE: ENABLE_NETWORK id=0
NetworkManager: <information>   wpa_supplicant(32710): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(32710): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(32710): RX ctrl_iface - hexdump_ascii(len=6):
NetworkManager: <information>   wpa_supplicant(32710):      41 54 54 41 43 48  ATTACH
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor attached - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(32710): Received 620 bytes of scan results (3 BSSes)
NetworkManager: <information>   wpa_supplicant(32710): Scan results: 3
NetworkManager: <information>   wpa_supplicant(32710): Selecting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(32710): 0: 00:14:6a:73:b5:00 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710): A/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 1: 00:14:6a:73:b7:80 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 2: e2:eb:84:d1:5f:ba ssid='yale wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x2
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710):    selected non-WPA AP 00:14:6a:73:b5:00 ssid='lighthouse'
NetworkManager: <information>   wpa_supplicant(32710): Trying to associate with 00:14:6a:73:b5:00 (SSID='lighthouse' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): Automatic auth_alg selection: 0x1
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP WPA IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): State: SCANNING -> ASSOCIATING
NetworkManager: <information>   wpa_supplicant(32710): Association request to the driver failed
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Setting authentication timeout: 5 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): : External notification - portControl=ForceAuthorized
NetworkManager: <information>   wpa_supplicant(32710): Authentication with 00:00:00:00:00:00 timed out.
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Added BSSID 00:00:00:00:00:00 into blacklist
NetworkManager: <information>   wpa_supplicant(32710): State: ASSOCIATING -> DISCONNECTED
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(32710): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(32710): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(32710): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(32710): Received 620 bytes of scan results (3 BSSes)
NetworkManager: <information>   wpa_supplicant(32710): Scan results: 3
NetworkManager: <information>   wpa_supplicant(32710): Selecting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(32710): 0: 00:14:6a:73:b5:00 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 1: 00:14:6a:73:b7:80 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 2: e2:eb:84:d1:5f:ba ssid='yale wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x2
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710):  selected non-WPA AP 00:14:6a:73:b5:00 ssid='lighthouse'
NetworkManager: <information>   wpa_supplicant(32710): Trying to associate with 00:14:6a:73:b5:00 (SSID='lighthouse' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): Automatic auth_alg selection: 0x1
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP WPA IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): State: SCANNING -> ASSOCIATING
NetworkManager: <information>   wpa_supplicant(32710): Association request to the driver failed
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Setting authentication timeout: 5 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portControl=ForceAuthorized
NetworkManager: <information>   wpa_supplicant(32710): Authentication with 00:00:00:00:00:00 timed out.
NetworkManager: <information>   wpa_supplicant(32710): 5 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): BSSID 00:00:00:00:00:00 blacklist count incremented to 2
NetworkManager: <information>   wpa_supplicant(32710): State: ASSOCIATING -> DISCONNECTED
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(32710): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(32710): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(32710): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(32710): Received 620 bytes of scan results (3 BSSes)
NetworkManager: <information>   wpa_supplicant(32710): Scan results: 3
NetworkManager: <information>   wpa_supplicant(32710): Selecting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(32710): 0: 00:14:6a:73:b5:00 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 1: 00:14:6a:73:b7:80 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 2: e2:eb:84:d1:5f:ba ssid='yale wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x2
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710):    selected non-WPA AP 00:14:6a:73:b5:00 ssid='lighthouse'
NetworkManager: <information>   wpa_supplicant(32710): Trying to associate with 00:14:6a:73:b5:00 (SSID='lighthouse' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(32710): 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): Automatic auth_alg selection: 0x1
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP WPA IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): State: SCANNING -> ASSOCIATING
NetworkManager: <information>   wpa_supplicant(32710): Association request to the driver failed
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Setting authentication timeout: 5 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portControl=ForceAuthorized
NetworkManager: <information>   wpa_supplicant(32710): Authentication with 00:00:00:00:00:00 timed out.
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): BSSID 00:00:00:00:00:00 blacklist count incremented to 3
NetworkManager: <information>   wpa_supplicant(32710): State: ASSOCIATING -> DISCONNECTED
NetworkManager: <information>   wpa_supplicant(32710): learing
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(32710): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(32710): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(32710): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(32710): Received 393 bytes of scan results (2 BSSes)
NetworkManager: <information>   wpa_supplicant(32710): Scan results: 2
NetworkManager: <information>   wpa_supplicant(32710): Selecting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(32710): 0: 00:14:6a:73:b5:00 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 1: e2:eb:84:d1:5f:ba ssid='yale wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x2
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710):    selected non-WPA AP 00:14:6a:73:b5:00 ssid='lighthouse'
NetworkManager: <information>   wpa_supplicant(32710): Trying to associate with 00:14:6a:73:b5:00 (SSID='lighthouse' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): Automatic auth_alg selection: 0x1
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP WPA IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): ured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): State: SCANNING -> ASSOCIATING
NetworkManager: <information>   wpa_supplicant(32710): Association request to the driver failed
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Setting authentication timeout: 5 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portControl=ForceAuthorized
NetworkManager: <information>   wpa_supplicant(32710): Authentication with 00:00:00:00:00:00 timed out.
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): BSSID 00:00:00:00:00:00 blacklist count incremented to 4
NetworkManager: <information>   wpa_supplicant(32710): State: ASSOCIATING -> DISCONNECTED
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(32710): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(32710): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(32710): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(32710): Received 393 bytes of scan results (2 BSSes)
NetworkManager: <information>   wpa_supplicant(32710): Scan results: 2
NetworkManager: <information>   wpa_supplicant(32710): cting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(32710): 0: 00:14:6a:73:b7:80 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 1: e2:eb:84:d1:5f:ba ssid='yale wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x2
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710):    selected non-WPA AP 00:14:6a:73:b7:80 ssid='lighthouse'
NetworkManager: <information>   wpa_supplicant(32710): Trying to associate with 00:14:6a:73:b7:80 (SSID='lighthouse' freq=2412 MHz)
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): Automatic auth_alg selection: 0x1
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP WPA IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): State: SCANNING -> ASSOCIATING
NetworkManager: <information>   wpa_supplicant(32710): Association request to the driver failed
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): out: 5 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portControl=ForceAuthorized
NetworkManager: <information>   wpa_supplicant(32710): Authentication with 00:00:00:00:00:00 timed out.
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): BSSID 00:00:00:00:00:00 blacklist count incremented to 5
NetworkManager: <information>   wpa_supplicant(32710): State: ASSOCIATING -> DISCONNECTED
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(32710): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(32710): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(32710): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(32710): Received 620 bytes of scan results (3 BSSes)
NetworkManager: <information>   wpa_supplicant(32710): Scan results: 3
NetworkManager: <information>   wpa_supplicant(32710): Selecting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(32710): 0: 00:14:6a:73:b5:00 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 1: 00:14:6a:73:b7:80 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): caps=0x2
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710):    selected non-WPA AP 00:14:6a:73:b5:00 ssid='lighthouse'
NetworkManager: <information>   wpa_supplicant(32710): Trying to associate with 00:14:6a:73:b5:00 (SSID='lighthouse' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): Automatic auth_alg selection: 0x1
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP WPA IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): State: SCANNING -> ASSOCIATING
NetworkManager: <information>   wpa_supplicant(32710): Association request to the driver failed
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Setting authentication timeout: 5 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portControl=ForceAuthorized
NetworkManager: <information>   wpa_supplicant(32710): Authentication with 00:00:00:00:00:00 timed out.
NetworkManager: <information>   wpa_supplicant(32710):  65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): BSSID 00:00:00:00:00:00 blacklist count incremented to 6
NetworkManager: <information>   wpa_supplicant(32710): State: ASSOCIATING -> DISCONNECTED
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(32710): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(32710): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(32710): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(32710): Received 620 bytes of scan results (3 BSSes)
NetworkManager: <information>   wpa_supplicant(32710): Scan results: 3
NetworkManager: <information>   wpa_supplicant(32710): Selecting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(32710): 0: 00:14:6a:73:b5:00 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 1: 00:14:6a:73:b7:80 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 2: e2:eb:84:d1:5f:ba ssid='yale wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x2
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710):    selected non-WPA AP 00:14:6a:73:b5:00 ssid='lighthouse'
NetworkManager: <information>   wpa_supplicant(32710): Trying to associate with 00:14:6a:73:b5:00 (SSID='lighthouse' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(32710): dump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): Automatic auth_alg selection: 0x1
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP WPA IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing AP RSN IE
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): No keys have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): State: SCANNING -> ASSOCIATING
NetworkManager: <information>   wpa_supplicant(32710): Association request to the driver failed
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Setting authentication timeout: 5 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portControl=ForceAuthorized
NetworkManager: <information>   wpa_supplicant(32710): Authentication with 00:00:00:00:00:00 timed out.
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): BSSID 00:00:00:00:00:00 blacklist count incremented to 7
NetworkManager: <information>   wpa_supplicant(32710): State: ASSOCIATING -> DISCONNECTED
NetworkManager: <information>   wpa_supplicant(32710): s have been configured - skip key clearing
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portEnabled=0
NetworkManager: <information>   wpa_supplicant(32710): EAPOL: External notification - portValid=0
NetworkManager: <information>   wpa_supplicant(32710): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(32710): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(32710): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(32710): Scan timeout - try to get results
NetworkManager: <information>   wpa_supplicant(32710): Received 620 bytes of scan results (3 BSSes)
NetworkManager: <information>   wpa_supplicant(32710): Scan results: 3
NetworkManager: <information>   wpa_supplicant(32710): Selecting BSS from priority group 0
NetworkManager: <information>   wpa_supplicant(32710): 0: 00:14:6a:73:b5:00 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 1: 00:14:6a:73:b7:80 ssid='lighthouse' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710): 2: e2:eb:84:d1:5f:ba ssid='yale wireless' wpa_ie_len=0 rsn_ie_len=0 caps=0x2
NetworkManager: <information>   wpa_supplicant(32710):    skip - no WPA/RSN IE
NetworkManager: <information>   wpa_supplicant(32710):    selected non-WPA AP 00:14:6a:73:b5:00 ssid='lighthouse'
NetworkManager: <information>   wpa_supplicant(32710): Trying to associate with 00:14:6a:73:b5:00 (SSID='lighthouse' freq=2437 MHz)
NetworkManager: <information>   wpa_supplicant(32710): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 33 32 36 34 33 2d 31 00 00 00
NetworkManager: <information>   wpa_supplicant(32710): Cancelling scan request
NetworkManager: <information>   wpa_supplicant(32710): WPA: clearing own WPA/RSN IE
NetworkManager: <information>   Activation (wlan0/wireless): association took too long (>60s), failing activation.
NetworkManager: <information>   Activation (wlan0) failure scheduled...
NetworkManager: <information>   Activation (wlan0) failed for access point (lighthouse)
NetworkManager: <information>   Activation (wlan0) failed.
NetworkManager: <information>   Deactivating device wlan0.
Failed to disable WPA in the driver.
NetworkManager: <information>   SWITCH: no current connection, found better connection 'eth0'.

```

---

### Post by Stoph on 2006-10-12
I give up for now... I can switch pretty easily if I use the built-in networking configuration tools

---

### Post by MattinTucson on 2007-09-21
I'm running into the same problem with an Inspiron 1500n, stock ubuntu with updates.  Network manager shows I'm getting a consistent 80-90% signal from my works "guest" wireless network.  This is a totally open network - no passwords or such. I left-click on the network manager applet, click on my works guest network, and then it sits and spins for a minute, after which it doesn't connect.  For testing purposes, I have done this 20+ times each day the past two days.  I connected once yesterday this way, though I don't know what was different. Today I tried fiddling with manual configuration and it somehow worked when I tried to start my own network then clicked on the guest network.  

Now, compare this to wifi-Radar.  It spins for a second, gets an address for a few more, then I am on.  It works the first time, and every time.  

I am guessing it is some configuration problems with Network Manager.  I have tried connecting to other networks before when they have signals of well over 50%.  However, network manager will not connect.  I will have to retry them with wifi-radar. 

I would prefer to get things working with NetworkManager due to net-aware applications.  Banshee won't report, and Evolution complains when I connect with WiFi Radar.

Hope somebody knows what is up.  I'm thinking of switching to a KDE-based distro just so I don't have to deal with NetworkManager.  Connecting to open networks should be what it is all about.

---

### Post by MattinTucson on 2007-09-28
I have found a work-around I can use at my company.  I'm not sure it will work with other signals that are not as strong.

The work-around is to simply turn the wi-fi off, then turn it back on, Fn-F2 on my laptop.  When I turn it back on, it comes right up.

So, I think it is pretty clear that it is some problem with network manager, and not a signal issue.  I've also had some problems with Network Manager finding my modem when I use dial-up.  I think Network manager has some configuration problems that no one can figure out how to really fix.

---

