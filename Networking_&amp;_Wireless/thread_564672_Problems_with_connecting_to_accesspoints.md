---
title: "Problems with connecting to accesspoints"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-10-01
Hey Forum. 

I have just moved and setup my network again. 

But having huge problems with the wireless network.
I know it's working caurse my boy can connect from Winblows.  I have earliere been able to connect to it - but now nothing seems to help - and getting this in my log - allthough its pretty funny - caurse my network is working 7all other places - ANd have testet this with 2 different AP at home - D-link DWL+2000AP & Linksys W54G ! 

Here's the logfile - what is going wrong??? 
```

Oct  1 18:25:37 ubuntu-pbj dhclient: DHCPREQUEST on eth0 to 172.16.0.1 port 67
Oct  1 18:25:54 ubuntu-pbj dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct  1 18:26:06 ubuntu-pbj NetworkManager: <debug info>^I[1191255966.650547] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'pbj-it' 
Oct  1 18:26:06 ubuntu-pbj NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth0 / pbj-it 
Oct  1 18:26:06 ubuntu-pbj NetworkManager: <information>^IDeactivating device eth0. 
Oct  1 18:26:06 ubuntu-pbj NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_essid (): error setting ESSID to '' for device eth0: Invalid argument 
Oct  1 18:26:06 ubuntu-pbj dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct  1 18:26:06 ubuntu-pbj NetworkManager: <information>^IDevice eth0 activation scheduled... 
Oct  1 18:26:06 ubuntu-pbj NetworkManager: <information>^IDeactivating device eth1. 
Oct  1 18:26:06 ubuntu-pbj dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6325
Oct  1 18:26:06 ubuntu-pbj dhclient: killed old client process, removed PID file
Oct  1 18:26:06 ubuntu-pbj dhclient: DHCPRELEASE on eth1 to 172.16.0.1 port 67
Oct  1 18:26:06 ubuntu-pbj avahi-daemon[5264]: Withdrawing address record for 172.16.0.83 on eth1.
Oct  1 18:26:06 ubuntu-pbj avahi-daemon[5264]: Leaving mDNS multicast group on interface eth1.IPv4 with address 172.16.0.83.
Oct  1 18:26:06 ubuntu-pbj avahi-daemon[5264]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct  1 18:26:06 ubuntu-pbj avahi-autoipd(eth1)[6632]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Oct  1 18:26:06 ubuntu-pbj avahi-autoipd(eth1)[6632]: Successfully called chroot().
Oct  1 18:26:06 ubuntu-pbj avahi-autoipd(eth1)[6632]: Successfully dropped root privileges.
Oct  1 18:26:06 ubuntu-pbj avahi-autoipd(eth1)[6632]: fopen() failed: Permission denied
Oct  1 18:26:06 ubuntu-pbj avahi-autoipd(eth1)[6632]: Starting with address 169.254.2.197
Oct  1 18:26:07 ubuntu-pbj avahi-daemon[5264]: Withdrawing address record for fe80::21c:23ff:fe8d:210b on eth1.
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) started... 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0/wireless): access point 'pbj-it' is unencrypted, no key needed. 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth0^I^Iwext^I/var/run/wpa_supplicant^I' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: response was 'OK' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: response was 'OK' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: response was '0' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 70626a2d6974' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: response was 'OK' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: response was 'OK' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^ISUP: response was 'OK' 
Oct  1 18:26:07 ubuntu-pbj kernel: [  263.946881] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Global control interface '/var/run/wpa_supplicant-global' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RX global ctrl_iface - hexdump_ascii(len=49): 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):      68 30 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h0__wext_/var/ru 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):      09                                                _                
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth0^I^Iwext^I/var/run/wpa_supplicant^I' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Initializing interface 'eth0' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' bridge 'N/A' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Initializing interface (2) 'eth0' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: SUPP_PAE entering state DISCONNECTED 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: SUPP_BE entering state INITIALIZE 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAP: EAP entering state DISABLED 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portEnabled=0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portValid=0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):   capabilities: key_mgmt 0xf enc 0xf 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WEXT: Operstate: linkmode=1, operstate=5 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): 9 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_wpa 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_countermeasures 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_drop_unencrypted 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting scan request: 0 sec 100000 usec 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Added interface eth0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b06 len=12 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RX ctrl_iface - hexdump_ascii(len=9): 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RX ctrl_iface - hexdump_ascii(len=11): 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE: ADD_NETWORK 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RX ctrl_iface - hexdump_ascii(len=31): [REMOVED] 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE: SET_NETWORK id=0 name='ssid' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE: value - hexdump_ascii(len=12): [REMOVED] 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): ssid - hexdump_ascii(len=6): 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):      70 62 6a 2d 69 74                                 pbj-it           
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): ce - hexdump_ascii(len=27): [REMOVED] 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE: value - hexdump_ascii(len=4): [REMOVED] 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): key_mgmt: 0x4 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RX ctrl_iface - hexdump_ascii(len=16): 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE: ENABLE_NETWORK id=0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting scan request: 0 sec 0 usec 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: DISCONNECTED -> SCANNING 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Starting AP scan (broadcast SSID) 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Trying to get current scan results first without requesting a new scan to speed up initial association 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Received 279 bytes of scan results (1 BSSes) 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Scan results: 1 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Selecting BSS from priority group 0 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): 0: 00:11:95:7c:1b:e8 ssid='pbj-it' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    skip - no WPA/RSN IE 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    selected non-WPA AP 00:11:95:7c:1b:e8 ssid='pbj-it' 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Trying to associate with 00:11:95:7c:1b:e8 (SSID='pbj-it' freq=2437 MHz) 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Cancelling scan request 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing own WPA/RSN IE 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Automatic auth_alg selection: 0x1 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing AP WPA IE 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing AP RSN IE 
Oct  1 18:26:07 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing own WPA/RSN IE 
Oct  1 18:26:11 ubuntu-pbj dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct  1 18:26:12 ubuntu-pbj avahi-autoipd(eth1)[6632]: Callout BIND, address 169.254.2.197 on interface eth1
Oct  1 18:26:12 ubuntu-pbj avahi-daemon[5264]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.2.197.
Oct  1 18:26:12 ubuntu-pbj avahi-daemon[5264]: New relevant interface eth1.IPv4 for mDNS.
Oct  1 18:26:12 ubuntu-pbj avahi-daemon[5264]: Registering new address record for 169.254.2.197 on eth1.IPv4.
Oct  1 18:26:16 ubuntu-pbj avahi-autoipd(eth1)[6632]: Successfully claimed IP address 169.254.2.197
Oct  1 18:26:16 ubuntu-pbj avahi-autoipd(eth1)[6632]: fopen() failed: Permission denied
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): ring 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_drop_unencrypted 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: SCANNING -> ASSOCIATING 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WEXT: Operstate: linkmode=-1, operstate=5 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_associate 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting authentication timeout: 10 sec 0 usec 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portControl=ForceAuthorized 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE monitor attached - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 34 36 2d 34 00 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b06 len=12 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b04 len=16 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b1a len=22 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Authentication with 00:00:00:00:00:00 timed out. 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 34 36 2d 34 00 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Added BSSID 00:11:95:7c:1b:e8 into blacklist 
Oct  1 18:26:17 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: ASSOCIATING -> DISCONNECTED 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): xt_set_operstate: operstate 0->0 (DORMANT) 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WEXT: Operstate: linkmode=-1, operstate=5 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): No keys have been configured - skip key clearing 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portEnabled=0 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portValid=0 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting scan request: 0 sec 0 usec 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: DISCONNECTED -> SCANNING 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Starting AP scan (broadcast SSID) 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Scan timeout - try to get results 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Received 279 bytes of scan results (1 BSSes) 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Scan results: 1 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Selecting BSS from priority group 0 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): 0: 00:11:95:7c:1b:e8 ssid='pbj-it' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    skip - no WPA/RSN IE 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    selected non-WPA AP 00:11:95:7c:1b:e8 ssid='pbj-it' 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Trying to associate with 00:11:95:7c:1b:e8 (SSID='pbj-it' freq=2437 MHz) 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 34 36 2d 34 00 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Cancelling scan request 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing own WPA/RSN IE 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Automatic auth_alg selection: 0x1 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing AP WPA IE 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing AP RSN IE 
Oct  1 18:26:20 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing own WPA/RSN IE 
Oct  1 18:26:20 ubuntu-pbj kernel: [  269.149316] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Oct  1 18:26:27 ubuntu-pbj dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): nfigured - skip key clearing 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_drop_unencrypted 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: SCANNING -> ASSOCIATING 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WEXT: Operstate: linkmode=-1, operstate=5 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_associate 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting authentication timeout: 10 sec 0 usec 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portControl=ForceAuthorized 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b06 len=12 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b04 len=16 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b1a len=22 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Authentication with 00:00:00:00:00:00 timed out. 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 34 36 2d 34 00 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): BSSID 00:11:95:7c:1b:e8 blacklist count incremented to 2 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: ASSOCIATING -> DISCONNECTED 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Oct  1 18:26:30 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WEXT: Operstate: linkmode=-1, operstate=5 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): ng 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portEnabled=0 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portValid=0 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting scan request: 0 sec 0 usec 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: DISCONNECTED -> SCANNING 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Starting AP scan (broadcast SSID) 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Scan timeout - try to get results 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Received 279 bytes of scan results (1 BSSes) 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Scan results: 1 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Selecting BSS from priority group 0 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): 0: 00:11:95:7c:1b:e8 ssid='pbj-it' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    skip - blacklisted 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): No APs found - clear blacklist and try again 
Oct  1 18:26:33 ubuntu-pbj kernel: [  274.350855] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Removed BSSID 00:11:95:7c:1b:e8 from blacklist (clear) 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Selecting BSS from priority group 0 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): 0: 00:11:95:7c:1b:e8 ssid='pbj-it' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    skip - no WPA/RSN IE 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    selected non-WPA AP 00:11:95:7c:1b:e8 ssid='pbj-it' 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Trying to associate with 00:11:95:7c:1b:e8 (SSID='pbj-it' freq=2437 MHz) 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 34 36 2d 34 00 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Cancelling scan request 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing own WPA/RSN IE 
Oct  1 18:26:33 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Automatic auth_alg selection: 0x1 
Oct  1 18:26:39 ubuntu-pbj dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): earing AP WPA IE 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing AP RSN IE 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing own WPA/RSN IE 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): No keys have been configured - skip key clearing 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_drop_unencrypted 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: SCANNING -> ASSOCIATING 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WEXT: Operstate: linkmode=-1, operstate=5 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_associate 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting authentication timeout: 10 sec 0 usec 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portControl=ForceAuthorized 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b06 len=12 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b04 len=16 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b1a len=22 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Authentication with 00:00:00:00:00:00 timed out. 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 34 36 2d 34 00 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Added BSSID 00:11:95:7c:1b:e8 into blacklist 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: ASSOCIATING -> DISCONNECTED 
Oct  1 18:26:43 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): state: linkmode=-1, operstate=5 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): No keys have been configured - skip key clearing 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portEnabled=0 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portValid=0 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting scan request: 0 sec 0 usec 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: DISCONNECTED -> SCANNING 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Starting AP scan (broadcast SSID) 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Scan timeout - try to get results 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Received 279 bytes of scan results (1 BSSes) 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Scan results: 1 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Selecting BSS from priority group 0 
Oct  1 18:26:46 ubuntu-pbj kernel: [  284.257813] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): 0: 00:11:95:7c:1b:e8 ssid='pbj-it' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    skip - no WPA/RSN IE 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    selected non-WPA AP 00:11:95:7c:1b:e8 ssid='pbj-it' 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Trying to associate with 00:11:95:7c:1b:e8 (SSID='pbj-it' freq=2437 MHz) 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 34 36 2d 34 00 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Cancelling scan request 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing own WPA/RSN IE 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Automatic auth_alg selection: 0x1 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing AP WPA IE 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing AP RSN IE 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing own WPA/RSN IE 
Oct  1 18:26:46 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): No keys have been configured - skip key clearing 
Oct  1 18:26:52 ubuntu-pbj dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Oct  1 18:26:54 ubuntu-pbj avahi-autoipd(eth0)[6715]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Oct  1 18:26:54 ubuntu-pbj avahi-autoipd(eth0)[6715]: Successfully called chroot().
Oct  1 18:26:54 ubuntu-pbj avahi-autoipd(eth0)[6715]: Successfully dropped root privileges.
Oct  1 18:26:54 ubuntu-pbj avahi-autoipd(eth0)[6715]: fopen() failed: Permission denied
Oct  1 18:26:54 ubuntu-pbj avahi-autoipd(eth0)[6715]: Starting with address 169.254.4.149
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): _unencrypted 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: SCANNING -> ASSOCIATING 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WEXT: Operstate: linkmode=-1, operstate=5 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_associate 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting authentication timeout: 10 sec 0 usec 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portControl=ForceAuthorized 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b06 len=12 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b04 len=16 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Wireless event: cmd=0x8b1a len=22 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Authentication with 00:00:00:00:00:00 timed out. 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 34 36 2d 34 00 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): BSSID 00:11:95:7c:1b:e8 blacklist count incremented to 2 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: ASSOCIATING -> DISCONNECTED 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WEXT: Operstate: linkmode=-1, operstate=5 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): No keys have been configured - skip key clearing 
Oct  1 18:26:56 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): EAPOL: External notification - portEnabled=0 
Oct  1 18:26:59 ubuntu-pbj avahi-autoipd(eth0)[6715]: Callout BIND, address 169.254.4.149 on interface eth0
Oct  1 18:26:59 ubuntu-pbj avahi-daemon[5264]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.4.149.
Oct  1 18:26:59 ubuntu-pbj avahi-daemon[5264]: New relevant interface eth0.IPv4 for mDNS.
Oct  1 18:26:59 ubuntu-pbj avahi-daemon[5264]: Registering new address record for 169.254.4.149 on eth0.IPv4.
Oct  1 18:26:59 ubuntu-pbj avahi-autoipd(eth0)[6716]: Killing child.
Oct  1 18:26:59 ubuntu-pbj avahi-autoipd(eth0)[6716]: client: RTNETLINK answers: File exists
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): : External notification - portValid=0 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Setting scan request: 0 sec 0 usec 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): State: DISCONNECTED -> SCANNING 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Starting AP scan (broadcast SSID) 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Scan timeout - try to get results 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Received 279 bytes of scan results (1 BSSes) 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Scan results: 1 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Selecting BSS from priority group 0 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): 0: 00:11:95:7c:1b:e8 ssid='pbj-it' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    skip - blacklisted 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): No APs found - clear blacklist and try again 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Removed BSSID 00:11:95:7c:1b:e8 from blacklist (clear) 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Selecting BSS from priority group 0 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): 0: 00:11:95:7c:1b:e8 ssid='pbj-it' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    skip - no WPA/RSN IE 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638):    selected non-WPA AP 00:11:95:7c:1b:e8 ssid='pbj-it' 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Trying to associate with 00:11:95:7c:1b:e8 (SSID='pbj-it' freq=2437 MHz) 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 34 36 2d 34 00 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Cancelling scan request 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing own WPA/RSN IE 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): Automatic auth_alg selection: 0x1 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing AP WPA IE 
Oct  1 18:26:59 ubuntu-pbj NetworkManager: <information>^Iwpa_supplicant(6638): WPA: clearing AP RSN IE 
Oct  1 18:26:59 ubuntu-pbj kernel: [  290.525720] ndiswrapper (iw_set_freq:385): setting configuration failed (00010003)
Oct  1 18:27:03 ubuntu-pbj avahi-autoipd(eth0)[6715]: Successfully claimed IP address 169.254.4.149
Oct  1 18:27:03 ubuntu-pbj avahi-autoipd(eth0)[6715]: fopen() failed: Permission denied
Oct  1 18:27:03 ubuntu-pbj avahi-autoipd(eth0)[6715]: Got SIGTERM, quitting.
Oct  1 18:27:03 ubuntu-pbj avahi-autoipd(eth0)[6715]: Callout STOP, address 169.254.4.149 on interface eth0
Oct  1 18:27:03 ubuntu-pbj avahi-daemon[5264]: Withdrawing address record for 169.254.4.149 on eth0.
Oct  1 18:27:03 ubuntu-pbj avahi-daemon[5264]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.4.149.
Oct  1 18:27:03 ubuntu-pbj avahi-daemon[5264]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct  1 18:27:03 ubuntu-pbj avahi-autoipd(eth0)[6716]: client: RTNETLINK answers: No such process
Oct  1 18:27:04 ubuntu-pbj dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0/wireless): association took too long (>60s), failing activation. 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) failure scheduled... 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) failed for access point (pbj-it) 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth0) failed. 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IDeactivating device eth0. 
Oct  1 18:27:07 ubuntu-pbj dhclient: receive_packet failed on eth0: Network is down
Oct  1 18:27:07 ubuntu-pbj kernel: [  298.259747] bridge-eth0: disabling the bridge
Oct  1 18:27:07 ubuntu-pbj kernel: [  298.272160] bridge-eth0: down
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_essid (): error setting ESSID to '' for device eth0: Invalid argument 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth1'. 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IWill activate connection 'eth1'. 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IDevice eth1 activation scheduled... 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) started... 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) successful. 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct  1 18:27:07 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct  1 18:27:08 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Beginning DHCP transaction. 
Oct  1 18:27:08 ubuntu-pbj dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6847488
Oct  1 18:27:08 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct  1 18:27:08 ubuntu-pbj NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth1 
Oct  1 18:27:08 ubuntu-pbj avahi-autoipd(eth1)[6632]: Got SIGTERM, quitting.
Oct  1 18:27:08 ubuntu-pbj avahi-autoipd(eth1)[6632]: Callout STOP, address 169.254.2.197 on interface eth1
Oct  1 18:27:08 ubuntu-pbj avahi-daemon[5264]: Withdrawing address record for 169.254.2.197 on eth1.
Oct  1 18:27:08 ubuntu-pbj avahi-daemon[5264]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.2.197.
Oct  1 18:27:08 ubuntu-pbj avahi-daemon[5264]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct  1 18:27:08 ubuntu-pbj avahi-autoipd(eth1)[6633]: client: RTNETLINK answers: No such process
Oct  1 18:27:10 ubuntu-pbj NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth1 
Oct  1 18:27:11 ubuntu-pbj dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Oct  1 18:27:11 ubuntu-pbj dhclient: send_packet: Network is down
Oct  1 18:27:11 ubuntu-pbj dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Oct  1 18:27:12 ubuntu-pbj dhclient: DHCPOFFER from 172.16.0.1
Oct  1 18:27:12 ubuntu-pbj dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Oct  1 18:27:12 ubuntu-pbj dhclient: DHCPACK from 172.16.0.1
Oct  1 18:27:12 ubuntu-pbj avahi-daemon[5264]: Joining mDNS multicast group on interface eth1.IPv4 with address 172.16.0.83.
Oct  1 18:27:12 ubuntu-pbj avahi-daemon[5264]: New relevant interface eth1.IPv4 for mDNS.
Oct  1 18:27:12 ubuntu-pbj avahi-daemon[5264]: Registering new address record for 172.16.0.83 on eth1.IPv4.
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth1 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct  1 18:27:12 ubuntu-pbj dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct  1 18:27:12 ubuntu-pbj dhclient: bound to 172.16.0.83 -- renewal in 278 seconds.
Oct  1 18:27:12 ubuntu-pbj dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct  1 18:27:12 ubuntu-pbj dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^I  address 172.16.0.83 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^I  netmask 255.255.0.0 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^I  broadcast 172.16.255.255 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^I  gateway 172.16.0.1 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^I  nameserver 172.16.0.1 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^I  domain name 'pbj-design.dk' 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct  1 18:27:12 ubuntu-pbj NetworkManager: <information>^IActivation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct  1 18:27:12 ubuntu-pbj avahi-daemon[5264]: Withdrawing address record for 172.16.0.83 on eth1.
Oct  1 18:27:12 ubuntu-pbj avahi-daemon[5264]: Leaving mDNS multicast group on interface eth1.IPv4 with address 172.16.0.83.
Oct  1 18:27:12 ubuntu-pbj avahi-daemon[5264]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct  1 18:27:12 ubuntu-pbj avahi-daemon[5264]: Joining mDNS multicast group on interface eth1.IPv4 with address 172.16.0.83.
Oct  1 18:27:12 ubuntu-pbj avahi-daemon[5264]: New relevant interface eth1.IPv4 for mDNS.
Oct  1 18:27:12 ubuntu-pbj avahi-daemon[5264]: Registering new address record for 172.16.0.83 on eth1.IPv4.

```

I haven't got a clue and have resettet the AP several times and tried all things that I know of - so please help!

---

