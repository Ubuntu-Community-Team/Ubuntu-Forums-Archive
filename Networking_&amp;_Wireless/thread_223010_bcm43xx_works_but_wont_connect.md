---
title: "bcm43xx works but wont connect"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by ubun00b on 2006-07-25
lspci:
0000:02:02.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)

iwconfig:
eth1      IEEE 802.11b  ESSID:off/any  Nickname:"Broadcom 4301"
          Mode:Managed  Frequency=2.484 GHz  Access Point: <edit>
          Bit Rate=11 Mb/s   Tx-Power=16 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist eth1 scanning:
eth1      Scan completed :
          Cell 01 - Address: <edit>
                    ESSID:<edit>
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-143 dBm
                    Extra: Last beacon: 80ms ago

/var/log syslog info: ***Verbose I know, but it shows the whole process***

Jul 25 19:40:16 localhost NetworkManager: <information>^Imatch 
Jul 25 19:40:16 localhost NetworkManager: <debug info>^I[1153870816.955104] nm_device_802_11_wireless_get_activation_ap (): Forcing AP '<edit>' 
Jul 25 19:40:16 localhost NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth1 / <edit> 
Jul 25 19:40:16 localhost NetworkManager: <information>^IDeactivating device eth1. 
Jul 25 19:40:18 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jul 25 19:40:18 localhost NetworkManager: <information>^IDevice eth1 activation scheduled... 
Jul 25 19:40:18 localhost NetworkManager: <information>^IDeactivating device eth0. 
Jul 25 19:40:18 localhost dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jul 25 19:40:19 localhost NetworkManager: <information>^IActivation (eth1) started... 
Jul 25 19:40:19 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 25 19:40:19 localhost NetworkManager: <information>^Imatch 
Jul 25 19:40:19 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jul 25 19:40:19 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jul 25 19:40:19 localhost NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jul 25 19:40:19 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jul 25 19:40:19 localhost NetworkManager: <information>^IActivation (eth1/wireless): access point '<edit>' is unencrypted, no key needed. 
Jul 25 19:40:19 localhost NetworkManager: <information>^Imatch 
Jul 25 19:40:20 localhost last message repeated 7 times
Jul 25 19:40:20 localhost NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: response was '0' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid <edit>' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Jul 25 19:40:21 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jul 25 19:40:21 localhost NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Global control interface '/var/run/wpa_supplicant-global' 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): RX global ctrl_iface - hexdump_ascii(len=49): 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      68 31 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h1__wext_/var/ru 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      09                                                _                
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Initializing interface 'eth1' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Initializing interface (2) 'eth1' 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: SUPP_PAE entering state DISCONNECTED 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: SUPP_BE entering state INITIALIZE 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAP: EAP entering state DISABLED 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portEnabled=0 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portValid=0 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):   capabilities: key_mgmt 0xf enc 0xf 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Own MAC address: 00:90:4b:55:b3:32 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_set_wpa 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): =0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_set_countermeasures 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_set_drop_unencrypted 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Setting scan request: 0 sec 100000 usec 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Added interface eth1 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b06 len=8 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): RX ctrl_iface - hexdump_ascii(len=9): 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): RX ctrl_iface - hexdump_ascii(len=11): 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE: ADD_NETWORK 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): RX ctrl_iface - hexdump_ascii(len=33): 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      69 64 20 36 63 36 39 36 65 36 62 37 33 37 39 37   id 6c696e6b73797 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      33                                                3                
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE: SET_NETWORK id=0 name='ssid' value='<edit>' 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): ssid - hexdump_ascii(len=7): 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): 6e 6b 73 79 73                              linksys          
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): RX ctrl_iface - hexdump_ascii(len=27): 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      79 5f 6d 67 6d 74 20 4e 4f 4e 45                  y_mgmt NONE      
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' value='NONE' 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): key_mgmt: 0x4 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): RX ctrl_iface - hexdump_ascii(len=16): 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE: ENABLE_NETWORK id=0 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Setting scan request: 0 sec 0 usec 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: DISCONNECTED -> SCANNING 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Starting AP scan (broadcast SSID) 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): RX ctrl_iface - hexdump_ascii(len=6): 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):      41 54 54 41 43 48                                 ATTACH           
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE monitor attached - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 37 36 2d 31 31 00 00 00 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b19 len=8 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Received 190 bytes of scan results (1 BSSes) 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Scan results: 1 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Selecting BSS from priority group 0 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): 0 rsn_ie_len=0 caps=0x1 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):    skip - no WPA/RSN IE 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790):    selected non-WPA AP <edit> ssid='<edit>' 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Trying to associate with <edit> (SSID='<edit>' freq=0 MHz) 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 37 36 2d 31 31 00 00 00 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Cancelling scan request 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing own WPA/RSN IE 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Automatic auth_alg selection: 0x1 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing AP WPA IE 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing AP RSN IE 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing own WPA/RSN IE 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): No keys have been configured - skip key clearing 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_set_drop_unencrypted 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: SCANNING -> ASSOCIATING 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_associate 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Setting authentication timeout: 10 sec 0 usec 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portControl=ForceAuthorized 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b06 len=8 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b1a len=16 
Jul 25 19:40:31 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Authentication with 00:00:00:00:00:00 timed out. 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): 37 36 2d 31 31 00 00 00 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Added BSSID 00:00:00:00:00:00 into blacklist 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: ASSOCIATING -> DISCONNECTED 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): No keys have been configured - skip key clearing 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portEnabled=0 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portValid=0 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Setting scan request: 0 sec 0 usec 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: DISCONNECTED -> SCANNING 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Starting AP scan (broadcast SSID) 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b19 len=8 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Received 190 bytes of scan results (1 BSSes) 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Scan results: 1 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Selecting BSS from priority group 0 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): 0: <edit> ssid='<edit>' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790):    skip - no WPA/RSN IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790):    selected non-WPA AP <edit> ssid='<edit>' 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Trying to associate with <edit> (SSID='<edit>' freq=0 MHz) 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 37 36 2d 31 31 00 00 00 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Cancelling scan request 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing own WPA/RSN IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Automatic auth_alg selection: 0x1 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing AP WPA IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing AP RSN IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): RSN IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): No keys have been configured - skip key clearing 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_set_drop_unencrypted 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: SCANNING -> ASSOCIATING 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_associate 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Setting authentication timeout: 10 sec 0 usec 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portControl=ForceAuthorized 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b06 len=8 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b1a len=16 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Authentication with 00:00:00:00:00:00 timed out. 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 37 36 2d 31 31 00 00 00 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): BSSID 00:00:00:00:00:00 blacklist count incremented to 2 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: ASSOCIATING -> DISCONNECTED 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): No keys have been configured - skip key clearing 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portEnabled=0 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portValid=0 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Setting scan request: 0 sec 0 usec 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: DISCONNECTED -> SCANNING 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Starting AP scan (broadcast SSID) 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b19 len=8 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Received 190 bytes of scan results (1 BSSes) 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Scan results: 1 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Selecting BSS from priority group 0 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790):  ssid='<edit>' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790):    skip - no WPA/RSN IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790):    selected non-WPA AP <edit> ssid='<edit>' 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Trying to associate with <edit> (SSID='<edit>' freq=0 MHz) 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 37 36 2d 31 31 00 00 00 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Cancelling scan request 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing own WPA/RSN IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Automatic auth_alg selection: 0x1 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing AP WPA IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing AP RSN IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing own WPA/RSN IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): No keys have been configured - skip key clearing 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_set_drop_unencrypted 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: SCANNING -> ASSOCIATING 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): wpa_driver_wext_associate 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Setting authentication timeout: 10 sec 0 usec 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portControl=ForceAuthorized 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b06 len=8 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b1a len=16 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Authentication with 00:00:00:00:00:00 timed out. 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): 61 5f 63 74 72 6c 5f 34 35 37 36 2d 31 31 00 00 00 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): BSSID 00:00:00:00:00:00 blacklist count incremented to 3 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: ASSOCIATING -> DISCONNECTED 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): No keys have been configured - skip key clearing 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portEnabled=0 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): EAPOL: External notification - portValid=0 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Setting scan request: 0 sec 0 usec 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): State: DISCONNECTED -> SCANNING 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Starting AP scan (broadcast SSID) 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Wireless event: cmd=0x8b19 len=8 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Received 190 bytes of scan results (1 BSSes) 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Scan results: 1 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Selecting BSS from priority group 0 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790):    skip - no WPA/RSN IE  
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): CTRL_IFACE monitor send - hexdump(len=43): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 37 36 2d 31 31 00 00 00 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Cancelling scan request 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing own WPA/RSN IE 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): Automatic auth_alg selection: 0x1 
Jul 25 19:40:52 localhost NetworkManager: <information>^Iwpa_supplicant(7790): WPA: clearing AP WPA IE 
Jul 25 19:41:21 localhost NetworkManager: <information>^IActivation (eth1/wireless): association took too long (>60s), failing activation. 
Jul 25 19:41:21 localhost NetworkManager: <information>^IActivation (eth1) failure scheduled... 
Jul 25 19:41:21 localhost NetworkManager: <information>^IActivation (eth1) failed for access point  
Jul 25 19:41:21 localhost NetworkManager: <information>^IActivation (eth1) failed. 
Jul 25 19:41:21 localhost NetworkManager: <information>^IDeactivating device eth1. 
Jul 25 19:41:32 localhost kernel: [17183853.704000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132
Jul 25 19:41:32 localhost last message repeated 7 times
Jul 25 19:41:32 localhost kernel: [17183853.704000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1134

Using:
Network Manager to set up wireless connection.  it sees the network, has 100% signal strength, and is connecting to a Linksys WRT54GS v1.1 with latest firmware revision.  Additionally, the connection didn't work with the previous firmware.  I used fwcutter to install the drivers.  Sorry this is so long, but after spending the past 8 days trying to solve this (learning a lot about linux in the process) i absolutely need help and will offer any info i can!  Thanks everyone!  

:confused:

---

### Post by stmiller on 2006-08-04
> wpa_driver_wext

Looks like it's trying to use the wext driver, and not the broadcom driver. BUT- maybe that is desired. I don't know.

I'm trying to figure this out too. You can set the option of driver 'broadcom' when trying wpa from the command line, but it spits back that wpa was not compiled with broadcom support. I tried to compile the latest wpa from source, and it won't compile, claming huge broadcom errors.  I think maybe that's why it is packaged in ubuntu w/o the broadcom driver compiled in. It might not work just yet. But perhaps wext works for this wifi card?

This is a pain for me too, as I need wifi wpa2 in ubuntu.

---

