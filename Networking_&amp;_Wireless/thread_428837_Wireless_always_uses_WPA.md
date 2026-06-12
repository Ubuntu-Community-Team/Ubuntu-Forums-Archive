---
title: "Wireless always uses WPA"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by newguy1234 on 2007-04-30
I am having trouble connecting to non secure access points in feisty. 

I have a BCM4310 Broadcom wireless card. I installed/ran bcm43xx-fwcutter and my wireless card showed me access points and everything seemed happy. I then successfully connected to a access point that was secured with WPA. However, when I tried to connect to an open, unsecured access point, my wireless card failed to connect. 

Here is a snippet from my syslog (I am trying to connect to the 'mogasd' access point:

Apr 25 19:08:33 kurt-laptop NetworkManager: <debug info>^I[1177553313.089386] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'mogasd' 
Apr 25 19:08:33 kurt-laptop NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth1 / mogasd 
Apr 25 19:08:33 kurt-laptop NetworkManager: <information>^IDeactivating device eth1. 
Apr 25 19:08:33 kurt-laptop avahi-daemon[5111]: Withdrawing address record for 169.254.4.147 on eth1.
Apr 25 19:08:33 kurt-laptop avahi-daemon[5111]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.4.147.
Apr 25 19:08:33 kurt-laptop avahi-daemon[5111]: Interface eth1.IPv4 no longer relevant for mDNS.
Apr 25 19:08:33 kurt-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Apr 25 19:08:33 kurt-laptop NetworkManager: <information>^IDevice eth1 activation scheduled... 
Apr 25 19:08:33 kurt-laptop NetworkManager: <information>^IDeactivating device eth0. 
Apr 25 19:08:33 kurt-laptop kernel: [ 1135.772000] SoftMAC: Open Authentication completed with 00:0f:b5:ee:10:e4
Apr 25 19:08:33 kurt-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 7612
Apr 25 19:08:33 kurt-laptop dhclient: killed old client process, removed PID file
Apr 25 19:08:33 kurt-laptop kernel: [ 1135.776000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr 25 19:08:33 kurt-laptop dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Apr 25 19:08:33 kurt-laptop avahi-daemon[5111]: Withdrawing address record for 192.168.1.4 on eth0.
Apr 25 19:08:33 kurt-laptop avahi-daemon[5111]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.4.
Apr 25 19:08:33 kurt-laptop avahi-daemon[5111]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 25 19:08:33 kurt-laptop avahi-autoipd(eth0)[7756]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Apr 25 19:08:33 kurt-laptop avahi-autoipd(eth0)[7756]: Successfully called chroot().
Apr 25 19:08:33 kurt-laptop avahi-autoipd(eth0)[7756]: Successfully dropped root privileges.
Apr 25 19:08:33 kurt-laptop avahi-autoipd(eth0)[7756]: fopen() failed: Permission denied
Apr 25 19:08:33 kurt-laptop avahi-autoipd(eth0)[7756]: Starting with address 169.254.9.183
Apr 25 19:08:34 kurt-laptop avahi-daemon[5111]: Withdrawing address record for fe80::218:8bff:feb6:ed8a on eth0.
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^IActivation (eth1) started... 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^IActivation (eth1/wireless): access point 'mogasd' is unencrypted, no key needed. 
Apr 25 19:08:34 kurt-laptop avahi-daemon[5111]: Registering new address record for fe80::219:7dff:fe59:2f58 on eth1.*.
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: response was '0' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 6d6f67617364' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Global control interface '/var/run/wpa_supplicant-global' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RX global ctrl_iface - hexdump_ascii(len=49): 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):      68 31 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h1__wext_/var/ru 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):      09                                                _                
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Initializing interface 'eth1' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' bridge 'N/A' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Initializing interface (2) 'eth1' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: SUPP_PAE entering state DISCONNECTED 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: SUPP_BE entering state INITIALIZE 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAP: EAP entering state DISABLED 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portEnabled=0 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portValid=0 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):   capabilities: key_mgmt 0xf enc 0xf 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WEXT: Operstate: linkmode=1, operstate=5 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): 8 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_wpa 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_countermeasures 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_drop_unencrypted 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting scan request: 0 sec 100000 usec 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Added interface eth1 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b06 len=8 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RX ctrl_iface - hexdump_ascii(len=9): 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RX ctrl_iface - hexdump_ascii(len=11): 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE: ADD_NETWORK 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RX ctrl_iface - hexdump_ascii(len=31): [REMOVED] 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE: SET_NETWORK id=0 name='ssid' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): =12): [REMOVED] 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): ssid - hexdump_ascii(len=6): 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):      6d 6f 67 61 73 64                                 mogasd           
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RX ctrl_iface - hexdump_ascii(len=27): [REMOVED] 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE: value - hexdump_ascii(len=4): [REMOVED] 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): key_mgmt: 0x4 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RX ctrl_iface - hexdump_ascii(len=16): 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE: ENABLE_NETWORK id=0 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting scan request: 0 sec 0 usec 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: DISCONNECTED -> SCANNING 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Starting AP scan (broadcast SSID) 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Trying to get current scan results first without requesting a new scan to speed up initial association 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Received 220 bytes of scan results (1 BSSes) 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Scan results: 1 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Selecting BSS from priority group 0 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): 0: 00:0f:b5:ee:10:e4 ssid='mogasd' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    skip - no WPA/RSN IE 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    selected non-WPA AP 00:0f:b5:ee:10:e4 ssid='mogasd' 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Trying to associate with 00:0f:b5:ee:10:e4 (SSID='mogasd' freq=0 MHz) 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Cancelling scan request 
Apr 25 19:08:34 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing own WPA/RSN IE 
Apr 25 19:08:38 kurt-laptop avahi-autoipd(eth0)[7756]: Callout BIND, address 169.254.9.183 on interface eth0
Apr 25 19:08:38 kurt-laptop avahi-daemon[5111]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.9.183.
Apr 25 19:08:38 kurt-laptop avahi-daemon[5111]: New relevant interface eth0.IPv4 for mDNS.
Apr 25 19:08:38 kurt-laptop avahi-daemon[5111]: Registering new address record for 169.254.9.183 on eth0.IPv4.
Apr 25 19:08:42 kurt-laptop avahi-autoipd(eth0)[7756]: Successfully claimed IP address 169.254.9.183
Apr 25 19:08:42 kurt-laptop avahi-autoipd(eth0)[7756]: fopen() failed: Permission denied
Apr 25 19:08:43 kurt-laptop kernel: [ 1145.844000] eth1: no IPv6 routers present
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):  
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing AP WPA IE 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing AP RSN IE 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing own WPA/RSN IE 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): No keys have been configured - skip key clearing 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_drop_unencrypted 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: SCANNING -> ASSOCIATING 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_associate 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting authentication timeout: 10 sec 0 usec 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portControl=ForceAuthorized 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE monitor attached - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 39 33 2d 31 34 00 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b06 len=8 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b1a len=14 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Authentication with 00:00:00:00:00:00 timed out. 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 39 33 2d 31 34 00 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): e4 into blacklist 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: ASSOCIATING -> DISCONNECTED 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): No keys have been configured - skip key clearing 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portEnabled=0 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portValid=0 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting scan request: 0 sec 0 usec 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: DISCONNECTED -> SCANNING 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Starting AP scan (broadcast SSID) 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b19 len=8 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Received 220 bytes of scan results (1 BSSes) 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Scan results: 1 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Selecting BSS from priority group 0 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): 0: 00:0f:b5:ee:10:e4 ssid='mogasd' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    skip - no WPA/RSN IE 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    selected non-WPA AP 00:0f:b5:ee:10:e4 ssid='mogasd' 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Trying to associate with 00:0f:b5:ee:10:e4 (SSID='mogasd' freq=0 MHz) 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 39 33 2d 31 34 00 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Cancelling scan request 
Apr 25 19:08:44 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing own WPA/RSN IE 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): c auth_alg selection: 0x1 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing AP WPA IE 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing AP RSN IE 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing own WPA/RSN IE 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): No keys have been configured - skip key clearing 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_drop_unencrypted 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: SCANNING -> ASSOCIATING 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_associate 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting authentication timeout: 10 sec 0 usec 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portControl=ForceAuthorized 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b06 len=8 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b1a len=14 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Authentication with 00:00:00:00:00:00 timed out. 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 39 33 2d 31 34 00 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): BSSID 00:0f:b5:ee:10:e4 blacklist count incremented to 2 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: ASSOCIATING -> DISCONNECTED 
Apr 25 19:08:54 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): e=-1, operstate=5 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): No keys have been configured - skip key clearing 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portEnabled=0 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portValid=0 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting scan request: 0 sec 0 usec 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: DISCONNECTED -> SCANNING 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Starting AP scan (broadcast SSID) 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b19 len=8 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Received 220 bytes of scan results (1 BSSes) 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Scan results: 1 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Selecting BSS from priority group 0 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): 0: 00:0f:b5:ee:10:e4 ssid='mogasd' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    skip - blacklisted 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): No APs found - clear blacklist and try again 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Removed BSSID 00:0f:b5:ee:10:e4 from blacklist (clear) 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Selecting BSS from priority group 0 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): 0: 00:0f:b5:ee:10:e4 ssid='mogasd' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    skip - no WPA/RSN IE 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    selected non-WPA AP 00:0f:b5:ee:10:e4 ssid='mogasd' 
Apr 25 19:08:55 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Trying to associate with 00:0f:b5:ee:10:e4 (SSID='mogasd' freq=0 MHz) 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): 74 72 6c 5f 35 30 39 33 2d 31 34 00 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Cancelling scan request 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing own WPA/RSN IE 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Automatic auth_alg selection: 0x1 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing AP WPA IE 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing AP RSN IE 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing own WPA/RSN IE 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): No keys have been configured - skip key clearing 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_drop_unencrypted 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: SCANNING -> ASSOCIATING 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_associate 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting authentication timeout: 10 sec 0 usec 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portControl=ForceAuthorized 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b06 len=8 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b1a len=14 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Authentication with 00:00:00:00:00:00 timed out. 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 39 33 2d 31 34 00 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Added BSSID 00:0f:b5:ee:10:e4 into blacklist 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTED 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): No keys have been configured - skip key clearing 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portEnabled=0 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portValid=0 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting scan request: 0 sec 0 usec 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: DISCONNECTED -> SCANNING 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Starting AP scan (broadcast SSID) 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b19 len=8 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Received 442 bytes of scan results (2 BSSes) 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Scan results: 2 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Selecting BSS from priority group 0 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): 0: 00:0f:b5:ee:10:e4 ssid='mogasd' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    skip - no WPA/RSN IE 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): 1: 00:16:b6:c5:de:47 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    skip - no WPA/RSN IE 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763):    selected non-WPA AP 00:0f:b5:ee:10:e4 ssid='mogasd' 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Trying to associate with 00:0f:b5:ee:10:e4 (SSID='mogasd' freq=0 MHz) 
Apr 25 19:09:05 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 39 33 2d 31 34 00 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): request 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing own WPA/RSN IE 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Automatic auth_alg selection: 0x1 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing AP WPA IE 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing AP RSN IE 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WPA: clearing own WPA/RSN IE 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): No keys have been configured - skip key clearing 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_drop_unencrypted 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: SCANNING -> ASSOCIATING 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): wpa_driver_wext_associate 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting authentication timeout: 10 sec 0 usec 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portControl=ForceAuthorized 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b06 len=8 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Wireless event: cmd=0x8b1a len=14 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Authentication with 00:00:00:00:00:00 timed out. 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): CTRL_IFACE monitor send - hexdump(len=41): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 39 33 2d 31 34 00 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): BSSID 00:0f:b5:ee:10:e4 blacklist count incremented to 2 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: ASSOCIATING -> DISCONNECTED 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): state 0->0 (DORMANT) 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): WEXT: Operstate: linkmode=-1, operstate=5 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): No keys have been configured - skip key clearing 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portEnabled=0 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): EAPOL: External notification - portValid=0 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): Setting scan request: 0 sec 0 usec 
Apr 25 19:09:15 kurt-laptop NetworkManager: <information>^Iwpa_supplicant(7763): State: DISCONNECTED -> SCANNING

Any thoughts or suggestions or help would be great. I can post more information if it will help solve the problem thanks!

---

