---
title: "Weird problem with AR5211"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by takeda on 2007-09-22
Hello, I got a laptop from my neighbour recently.
It appears it uses a network card with AR5211 chipset. The card appears to work well in Windows XP, but of course it doesn't work on Ubuntu 7.04 (that's why I'm asking for help).
Besides this card Ubuntu didn't have any problems with other drivers, unlike the Windows.

Anyway, Ubuntu seems to recognize the card, and even loads a proprietary driver, but the network manager, doesn't seem to pick up any Access Points, even when I try to manually connect to mine (that uses WPA) it doesn't seem to work :(((
Basically it tries for a minute or two and then gives up.

I was experimenting a little bit, and I uninstalled the proprietary drivers, and installed ndiswrapper + windows driver.
Still no luck.

What I noticed is that with the proprietary driver:
iwlist ath0 scan
Returns right away that no APs were found (it doesn't even cares if the network card is enabled or not)
With ndisdriver, at least it thinks a little bit, and when card is disabled it also displays an error, so at least I see it's trying to do something.

Today I was experimenting a bit, I set up Kismet with:
source=madwifi_ab,wifi0,Atheros_WiFi

and... Kismet nicely showed me my & my neighbors AP, so the card is definitively accessible.
Only thing is that it freezes after short while...

Here is log from connecting to my AP (using the standard proprietary driver, not ndiswrapper):
```
Sep 22 19:35:20 TKDLAPU NetworkManager: <debug info>^I[1190514920.053359] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'mayumi-ap' 
Sep 22 19:35:20 TKDLAPU NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/ath0 / mayumi-ap 
Sep 22 19:35:20 TKDLAPU NetworkManager: <information>^IDeactivating device ath0. 
Sep 22 19:35:20 TKDLAPU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Sep 22 19:35:20 TKDLAPU NetworkManager: <information>^IDevice ath0 activation scheduled... 
Sep 22 19:35:20 TKDLAPU NetworkManager: <information>^IDeactivating device eth0. 
Sep 22 19:35:20 TKDLAPU dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 4806
Sep 22 19:35:20 TKDLAPU dhclient: killed old client process, removed PID file
Sep 22 19:35:20 TKDLAPU dhclient: wifi0: unknown hardware address type 801
Sep 22 19:35:20 TKDLAPU dhclient: wifi0: unknown hardware address type 801
Sep 22 19:35:20 TKDLAPU dhclient: DHCPRELEASE on eth0 to 10.0.0.1 port 67
Sep 22 19:35:20 TKDLAPU avahi-daemon[4723]: Withdrawing address record for 10.0.0.192 on eth0.
Sep 22 19:35:20 TKDLAPU avahi-daemon[4723]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.0.192.
Sep 22 19:35:20 TKDLAPU avahi-daemon[4723]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 22 19:35:20 TKDLAPU avahi-autoipd(eth0)[5695]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Sep 22 19:35:20 TKDLAPU avahi-autoipd(eth0)[5695]: Successfully called chroot().
Sep 22 19:35:20 TKDLAPU avahi-autoipd(eth0)[5695]: Successfully dropped root privileges.
Sep 22 19:35:20 TKDLAPU avahi-autoipd(eth0)[5695]: fopen() failed: Permission denied
Sep 22 19:35:20 TKDLAPU avahi-autoipd(eth0)[5695]: Starting with address 169.254.4.100
Sep 22 19:35:21 TKDLAPU avahi-daemon[4723]: Withdrawing address record for fe80::203:25ff:fe06:a748 on eth0.
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) started... 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) Stage 1 of 5 (Device Prepare) started... 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) Stage 2 of 5 (Device Configure) starting... 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^IActivation (ath0/wireless): access point 'mayumi-ap' is encrypted, and a key exists.  No new key needed. 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant^I' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: response was 'OK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: sending command 'AP_SCAN 2' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: response was 'OK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: response was '0' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 6d6179756d692d6170' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: response was 'OK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: response was 'OK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 proto WPA' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: response was 'OK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: response was 'OK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 psk <key>' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: response was 'OK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^ISUP: response was 'OK' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) Stage 2 of 5 (Device Configure) complete. 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Global control interface '/var/run/wpa_supplicant-global' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RX global ctrl_iface - hexdump_ascii(len=52): 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 61 74   INTERFACE_ADD at 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700):      68 30 09 09 6d 61 64 77 69 66 69 09 2f 76 61 72   h0__madwifi_/var 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700):      2f 72 75 6e 2f 77 70 61 5f 73 75 70 70 6c 69 63   /run/wpa_supplic 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700):      61 6e 74 09                                       ant_             
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE GLOBAL INTERFACE_ADD 'ath0^I^Imadwifi^I/var/run/wpa_supplicant^I' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Initializing interface 'ath0' conf 'N/A' driver 'madwifi' ctrl_interface '/var/run/wpa_supplicant' bridge 'N/A' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Initializing interface (2) 'ath0' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: SUPP_PAE entering state DISCONNECTED 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: SUPP_BE entering state INITIALIZE 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAP: EAP entering state DISABLED 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: External notification - portEnabled=0 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: External notification - portValid=0 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): SIOCGIWRANGE: WE(compiled)=21 WE(source)=13 enc_capa=0xf 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700):   capabilities: key_mgmt 0xf enc 0xf 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WEXT: Operstate: linkmode=1, operstate=5 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): d:95:da 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_madwifi_del_key: keyidx=0 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_madwifi_del_key: keyidx=1 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_madwifi_del_key: keyidx=2 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_madwifi_del_key: keyidx=3 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_madwifi_set_countermeasures: enabled=0 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_madwifi_set_drop_unencrypted: enabled=1 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Setting scan request: 0 sec 100000 usec 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Added interface ath0 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Wireless event: cmd=0x8b06 len=8 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RX ctrl_iface - hexdump_ascii(len=9): 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700):      41 50 5f 53 43 41 4e 20 32                        AP_SCAN 2        
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RX ctrl_iface - hexdump_ascii(len=11): 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: ADD_NETWORK 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RX ctrl_iface - hexdump_ascii(len=37): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: SET_NETWORK id=0 name='ssid' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: value - hexdump_ascii(len=18): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): ssid - hexdump_ascii(len=9): 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700):      6d 61 79 75 6d 69 2d 61 70                        mayumi-ap        
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): rl_iface - hexdump_ascii(len=25): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: SET_NETWORK id=0 name='scan_ssid' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: value - hexdump_ascii(len=1): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): scan_ssid=1 (0x1) 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RX ctrl_iface - hexdump_ascii(len=23): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: SET_NETWORK id=0 name='proto' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: value - hexdump_ascii(len=3): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): proto: 0x1 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RX ctrl_iface - hexdump_ascii(len=30): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: value - hexdump_ascii(len=7): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): key_mgmt: 0x2 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RX ctrl_iface - hexdump_ascii(len=82): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: SET_NETWORK id=0 name='psk' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: value - hexdump_ascii(len=64): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): PSK - hexdump(len=32): [REMOVED] 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): RX ctrl_iface - hexdump_ascii(len=16): 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE: ENABLE_NETWORK id=0 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Setting scan request: 0 sec 0 usec 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): State: DISCONNECTED -> SCANNING 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Trying to associate with SSID 'mayumi-ap' 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Cancelling scan request 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: clearing own WPA/RSN IE 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Automatic auth_alg selection: 0x1 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): ssociation info 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: Set cipher suites based on configuration 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2 proto 1 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: clearing AP WPA IE 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: clearing AP RSN IE 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: using GTK CCMP 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: using PTK CCMP 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: using KEY_MGMT WPA-PSK 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): No keys have been configured - skip key clearing 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_madwifi_set_drop_unencrypted: enabled=1 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): State: SCANNING -> ASSOCIATING 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WEXT: Operstate: linkmode=-1, operstate=5 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_madwifi_associate 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Setting authentication timeout: 60 sec 0 usec 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: External notification - EAP success=0 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: External notification - EAP fail=0 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: External notification - portControl=Auto 
Sep 22 19:35:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE monitor attached - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 37 30 35 2d 33 00 
Sep 22 19:35:21 TKDLAPU kernel: [  693.720000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
Sep 22 19:35:23 TKDLAPU avahi-daemon[4723]: Registering new address record for fe80::290:96ff:fe3d:95da on ath0.*.
Sep 22 19:35:26 TKDLAPU avahi-autoipd(eth0)[5695]: Callout BIND, address 169.254.4.100 on interface eth0
Sep 22 19:35:26 TKDLAPU avahi-daemon[4723]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.4.100.
Sep 22 19:35:26 TKDLAPU avahi-daemon[4723]: New relevant interface eth0.IPv4 for mDNS.
Sep 22 19:35:26 TKDLAPU avahi-daemon[4723]: Registering new address record for 169.254.4.100 on eth0.IPv4.
Sep 22 19:35:30 TKDLAPU avahi-autoipd(eth0)[5695]: Successfully claimed IP address 169.254.4.100
Sep 22 19:35:30 TKDLAPU avahi-autoipd(eth0)[5695]: fopen() failed: Permission denied
Sep 22 19:35:32 TKDLAPU kernel: [  704.492000] ath0: no IPv6 routers present
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): UP]) 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Wireless event: cmd=0x8b1a len=17 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Authentication with 00:00:00:00:00:00 timed out. 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 37 30 35 2d 33 00 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Added BSSID 00:00:00:00:00:00 into blacklist 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): State: ASSOCIATING -> DISCONNECTED 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WEXT: Operstate: linkmode=-1, operstate=5 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): No keys have been configured - skip key clearing 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: External notification - portEnabled=0 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): EAPOL: External notification - portValid=0 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Setting scan request: 0 sec 0 usec 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): State: DISCONNECTED -> SCANNING 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Trying to associate with SSID 'mayumi-ap' 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 37 30 35 2d 33 00 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Cancelling scan request 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: clearing own WPA/RSN IE 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): Automatic auth_alg selection: 0x1 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: No WPA/RSN IE available from association info 
Sep 22 19:36:21 TKDLAPU NetworkManager: <information>^Iwpa_supplicant(5700): WPA: Set cipher suites based on configuration 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (ath0/wireless): association took too long (>120s), failing activation. 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) failure scheduled... 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) failed for access point (mayumi-ap) 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (ath0) failed. 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IDeactivating device ath0. 
Sep 22 19:37:21 TKDLAPU avahi-daemon[4723]: Withdrawing address record for fe80::290:96ff:fe3d:95da on ath0.
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'. 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IWill activate connection 'eth0'. 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IDevice eth0 activation scheduled... 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) started... 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started... 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting... 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful. 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete. 
Sep 22 19:37:21 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Sep 22 19:37:22 TKDLAPU NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction. 
Sep 22 19:37:22 TKDLAPU dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Sep 22 19:37:22 TKDLAPU dhclient: wifi0: unknown hardware address type 801
Sep 22 19:37:22 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Sep 22 19:37:22 TKDLAPU NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0 
Sep 22 19:37:23 TKDLAPU avahi-autoipd(eth0)[5695]: Got SIGTERM, quitting.
Sep 22 19:37:23 TKDLAPU avahi-autoipd(eth0)[5695]: Callout STOP, address 169.254.4.100 on interface eth0
Sep 22 19:37:23 TKDLAPU avahi-daemon[4723]: Withdrawing address record for 169.254.4.100 on eth0.
Sep 22 19:37:23 TKDLAPU avahi-daemon[4723]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.4.100.
Sep 22 19:37:23 TKDLAPU avahi-daemon[4723]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 22 19:37:23 TKDLAPU avahi-autoipd(eth0)[5696]: client: RTNETLINK answers: No such process
Sep 22 19:37:24 TKDLAPU NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0 
Sep 22 19:37:24 TKDLAPU dhclient: wifi0: unknown hardware address type 801
Sep 22 19:37:27 TKDLAPU dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Sep 22 19:37:27 TKDLAPU dhclient: DHCPOFFER from 10.0.0.1
Sep 22 19:37:27 TKDLAPU dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 22 19:37:27 TKDLAPU dhclient: DHCPACK from 10.0.0.1
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.192.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: New relevant interface eth0.IPv4 for mDNS.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Registering new address record for 10.0.0.192 on eth0.IPv4.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Withdrawing address record for 10.0.0.192 on eth0.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.0.192.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.192.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: New relevant interface eth0.IPv4 for mDNS.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Registering new address record for 10.0.0.192 on eth0.IPv4.
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Sep 22 19:37:27 TKDLAPU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Sep 22 19:37:27 TKDLAPU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep 22 19:37:27 TKDLAPU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon: 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^I  address 10.0.0.192 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^I  netmask 255.255.255.0 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^I  broadcast 10.0.0.255 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^I  gateway 10.0.0.1 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^I  nameserver 10.0.0.1 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^I  domain name 'lan' 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Sep 22 19:37:27 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Withdrawing address record for 10.0.0.192 on eth0.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.0.192.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Interface eth0.IPv4 no longer relevant for mDNS.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.192.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: New relevant interface eth0.IPv4 for mDNS.
Sep 22 19:37:27 TKDLAPU avahi-daemon[4723]: Registering new address record for 10.0.0.192 on eth0.IPv4.
Sep 22 19:37:27 TKDLAPU dhclient: bound to 10.0.0.192 -- renewal in 20663 seconds.
Sep 22 19:37:28 TKDLAPU NetworkManager: <information>^IClearing nscd hosts cache. 
Sep 22 19:37:28 TKDLAPU NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Sep 22 19:37:28 TKDLAPU NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Sep 22 19:37:28 TKDLAPU NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Sep 22 19:37:28 TKDLAPU NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Sep 22 19:37:29 TKDLAPU ntpdate[5863]: adjust time server 91.189.94.145 offset -0.057701 sec
Sep 22 19:37:30 TKDLAPU avahi-daemon[4723]: Registering new address record for fe80::203:25ff:fe06:a748 on eth0.*.
Sep 22 19:37:37 TKDLAPU avahi-daemon[4723]: Registering new address record for fe80::290:96ff:fe3d:95da on ath0.*.
Sep 22 19:37:39 TKDLAPU kernel: [  831.148000] eth0: no IPv6 routers present
Sep 22 19:37:46 TKDLAPU kernel: [  838.000000] ath0: no IPv6 routers present
```

Please help.

---

### Post by takeda on 2007-10-13
anyone have idea, what the problem could be?

---

