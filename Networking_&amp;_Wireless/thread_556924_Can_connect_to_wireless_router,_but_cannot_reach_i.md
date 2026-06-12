---
title: "Can connect to wireless router, but cannot reach internet"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by PolishAlice on 2007-09-21
Hey Everyone,

Here is my situation:

I have a Dell Latititude X1

I have successfully used wireless internet on multiple networks, but I am no longer able to access the internet through my wireless router. 

I have a windows computer on a wired connection to the router, a windows laptop and the x1 (my ubuntu laptop). Both Windows computers can connect to the router and access the internet, but my ubuntu machine can only access the internet when it is plugged in via ethernet.

While connected to the router:
I can ping 127.0.0.1
I can ping the ip address of the computer (assigned by the router)
but i cannot ping the router itself

So far, I have disabled ipv6, I have commented out everything but the loopback in /etc/network/interfaces and I have switched to OpenDNS.

Here is some of the data that my computer is spitting out:

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Barlow"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:46:BF:62   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-24 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:46  Invalid misc:0   Missed beacon:5
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:F1:C8:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:CE:95:13  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fece:9513/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2113 (2.0 KiB)  TX bytes:13663 (13.3 KiB)
          Interrupt:5 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8218 (8.0 KiB)  TX bytes:8218 (8.0 KiB)
```

Lastly, here is what my syslog reports if i disconnect from the router and attempt to connect again:


```
Sep 21 23:35:21 pubiodelfuego NetworkManager: <debug info>^I[1190432121.501900] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'Barlow' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/eth1 / Barlow 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IDeactivating device eth1. 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IDevice eth1 activation scheduled... 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1) started... 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1/wireless): access point 'Barlow' is unencrypted, no key needed. 
Sep 21 23:35:21 pubiodelfuego kernel: [  957.185000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: response was 'OK' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: response was 'OK' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: response was '0' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 4261726c6f77' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: response was 'OK' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: response was 'OK' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^ISUP: response was 'OK' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Global control interface '/var/run/wpa_supplicant-global' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RX global ctrl_iface - hexdump_ascii(len=49): 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):      68 31 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h1__wext_/var/ru 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):      09                                                _                
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Initializing interface 'eth1' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' bridge 'N/A' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Initializing interface (2) 'eth1' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): EAPOL: SUPP_PAE entering state DISCONNECTED 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): EAPOL: SUPP_BE entering state INITIALIZE 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): EAP: EAP entering state DISABLED 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): EAPOL: External notification - portEnabled=0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): EAPOL: External notification - portValid=0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):   capabilities: key_mgmt 0xf enc 0xf 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): WEXT: Operstate: linkmode=1, operstate=5 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): 3 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_wpa 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_countermeasures 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_drop_unencrypted 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Setting scan request: 0 sec 100000 usec 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Added interface eth1 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Wireless event: cmd=0x8b06 len=8 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RX ctrl_iface - hexdump_ascii(len=9): 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RX ctrl_iface - hexdump_ascii(len=11): 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): CTRL_IFACE: ADD_NETWORK 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RX ctrl_iface - hexdump_ascii(len=31): [REMOVED] 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): CTRL_IFACE: SET_NETWORK id=0 name='ssid' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): CTRL_IFACE: value - hexdump_ascii(len=12): [REMOVED] 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): ssid - hexdump_ascii(len=6): 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):      42 61 72 6c 6f 77                                 Barlow           
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): e - hexdump_ascii(len=27): [REMOVED] 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): CTRL_IFACE: value - hexdump_ascii(len=4): [REMOVED] 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): key_mgmt: 0x4 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RX ctrl_iface - hexdump_ascii(len=16): 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): CTRL_IFACE: ENABLE_NETWORK id=0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Setting scan request: 0 sec 0 usec 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): State: DISCONNECTED -> SCANNING 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Starting AP scan (broadcast SSID) 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Trying to get current scan results first without requesting a new scan to speed up initial association 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Received 665 bytes of scan results (3 BSSes) 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Scan results: 3 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Selecting BSS from priority group 0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): 0: 00:13:46:88:f1:0c ssid='karin51' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):    skip - no WPA/RSN IE 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): 1: 00:14:6c:46:bf:62 ssid='Barlow' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):    skip - no WPA/RSN IE 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): 2: 00:13:10:b0:fb:5e ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):    skip - no WPA/RSN IE 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):    selected non-WPA AP 00:14:6c:46:bf:62 ssid='Barlow' 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Trying to associate with 00:14:6c:46:bf:62 (SSID='Barlow' freq=0 MHz) 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): st 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): WPA: clearing own WPA/RSN IE 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Automatic auth_alg selection: 0x1 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): WPA: clearing AP WPA IE 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): WPA: clearing AP RSN IE 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): WPA: clearing own WPA/RSN IE 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): No keys have been configured - skip key clearing 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_drop_unencrypted 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): State: SCANNING -> ASSOCIATING 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): WEXT: Operstate: linkmode=-1, operstate=5 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_associate 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Setting authentication timeout: 10 sec 0 usec 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): EAPOL: External notification - portControl=ForceAuthorized 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): CTRL_IFACE monitor attached - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 39 2d 38 00 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Wireless event: cmd=0x8b06 len=8 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Wireless event: cmd=0x8b1a len=14 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Wireless event: cmd=0x8b19 len=8 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Received 665 bytes of scan results (3 BSSes) 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Scan results: 3 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Selecting BSS from priority group 0 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'Barlow'. 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Sep 21 23:35:21 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Sep 21 23:35:21 pubiodelfuego kernel: [  957.498000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Beginning DHCP transaction. 
Sep 21 23:35:22 pubiodelfuego dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993440
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): id='karin51' wpa_ie_len=0 rsn_ie_len=0 caps=0x11 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):    skip - no WPA/RSN IE 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): 1: 00:14:6c:46:bf:62 ssid='Barlow' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):    skip - no WPA/RSN IE 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): 2: 00:13:10:b0:fb:5e ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):    skip - no WPA/RSN IE 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226):    selected non-WPA AP 00:14:6c:46:bf:62 ssid='Barlow' 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Already associated with the selected AP. 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP]) 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Wireless event: cmd=0x8b15 len=20 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Wireless event: new AP: 00:14:6c:46:bf:62 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): State: ASSOCIATING -> ASSOCIATED 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): WEXT: Operstate: linkmode=-1, operstate=5 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Associated to a new BSS: BSSID=00:14:6c:46:bf:62 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): Associated with 00:14:6c:46:bf:62 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 34 39 39 2d 38 00 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): WPA: Association event - clear replay counter 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): EAPOL: External notification - portEnabled=0 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^Iwpa_supplicant(6226): EAPOL: External notification - portValid=0 
Sep 21 23:35:22 pubiodelfuego NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth1 
Sep 21 23:35:23 pubiodelfuego avahi-daemon[4517]: Registering new address record for fe80::20e:35ff:fece:9513 on eth1.*.
Sep 21 23:35:23 pubiodelfuego NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth1 
Sep 21 23:35:24 pubiodelfuego dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Sep 21 23:35:31 pubiodelfuego dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Sep 21 23:35:32 pubiodelfuego kernel: [  967.965000] eth1: no IPv6 routers present
Sep 21 23:35:39 pubiodelfuego dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Sep 21 23:35:50 pubiodelfuego dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Sep 21 23:35:55 pubiodelfuego dhclient: No DHCPOFFERS received.
Sep 21 23:35:55 pubiodelfuego avahi-autoipd(eth1)[6272]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Sep 21 23:35:55 pubiodelfuego avahi-autoipd(eth1)[6272]: Successfully called chroot().
Sep 21 23:35:55 pubiodelfuego avahi-autoipd(eth1)[6272]: Successfully dropped root privileges.
Sep 21 23:35:55 pubiodelfuego avahi-autoipd(eth1)[6272]: fopen() failed: Permission denied
Sep 21 23:35:55 pubiodelfuego avahi-autoipd(eth1)[6272]: Starting with address 169.254.5.150
Sep 21 23:36:00 pubiodelfuego avahi-autoipd(eth1)[6272]: Callout BIND, address 169.254.5.150 on interface eth1
Sep 21 23:36:00 pubiodelfuego avahi-daemon[4517]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.5.150.
Sep 21 23:36:00 pubiodelfuego avahi-daemon[4517]: New relevant interface eth1.IPv4 for mDNS.
Sep 21 23:36:00 pubiodelfuego avahi-daemon[4517]: Registering new address record for 169.254.5.150 on eth1.IPv4.
Sep 21 23:36:00 pubiodelfuego avahi-autoipd(eth1)[6273]: client: RTNETLINK answers: File exists
Sep 21 23:36:04 pubiodelfuego avahi-autoipd(eth1)[6272]: Successfully claimed IP address 169.254.5.150
Sep 21 23:36:04 pubiodelfuego avahi-autoipd(eth1)[6272]: fopen() failed: Permission denied
Sep 21 23:36:04 pubiodelfuego NetworkManager: <information>^IDHCP daemon state is now 9 (fail) for interface eth1 
Sep 21 23:36:04 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Sep 21 23:36:04 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Timeout) started... 
Sep 21 23:36:04 pubiodelfuego NetworkManager: <information>^IActivation (eth1) failure scheduled... 
Sep 21 23:36:04 pubiodelfuego NetworkManager: <information>^IActivation (eth1) Stage 4 of 5 (IP Configure Timeout) complete. 
Sep 21 23:36:04 pubiodelfuego NetworkManager: <information>^IActivation (eth1) failed for access point (Barlow) 
Sep 21 23:36:04 pubiodelfuego NetworkManager: <information>^IActivation (eth1) failed. 
Sep 21 23:36:04 pubiodelfuego NetworkManager: <information>^IDeactivating device eth1. 
Sep 21 23:36:04 pubiodelfuego dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6243
Sep 21 23:36:04 pubiodelfuego dhclient: killed old client process, removed PID file
Sep 21 23:36:05 pubiodelfuego dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Sep 21 23:36:05 pubiodelfuego avahi-daemon[4517]: Withdrawing address record for 169.254.5.150 on eth1.
Sep 21 23:36:05 pubiodelfuego avahi-daemon[4517]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.5.150.
Sep 21 23:36:06 pubiodelfuego avahi-daemon[4517]: Interface eth1.IPv4 no longer relevant for mDNS.
Sep 21 23:36:06 pubiodelfuego avahi-daemon[4517]: Withdrawing address record for fe80::20e:35ff:fece:9513 on eth1.
Sep 21 23:36:06 pubiodelfuego avahi-autoipd(eth1)[6272]: SIOCSIFFLAGS failed: Permission denied
Sep 21 23:36:06 pubiodelfuego avahi-autoipd(eth1)[6272]: Callout STOP, address 169.254.5.150 on interface eth1
Sep 21 23:36:06 pubiodelfuego avahi-autoipd(eth1)[6273]: client: RTNETLINK answers: No such device
Sep 21 23:36:06 pubiodelfuego avahi-autoipd(eth1)[6273]: Script execution failed with return value 2
```

I came across a bug thread which recommended running the command:

```
sudo apt-get --purge install avahi-autoipd --reinstall
```

but this made no difference.

Thanks in advance, I will be back in the morning.
Let me know if this has already been answered somewhere I couldn't find it or if I should give more info.

---

### Post by noob12 on 2007-09-22
Your ifconfig shows ipv6 addresses so you haven't completely disabled ipv6.  Whatever you did to do that wasn't correct or complete.

If you want to disable that you should edit **/etc/modprobe.d/aliases**  and replace the
line **alias net-pf-10 ipv6** with this
```

# disabling ipv6
#alias net-pf-10 ipv6
alias net-pf-10 off
alias ipv6 off
# end disabling ipv6

```

Save. Then reboot.

Connect wireless.  Assuming you still have the problem, can you please post the output of ```
route -n
```

Your eth0 is up at the same time, but with no address.  Do you see any routes associated with eth0 (last column) of the **route -n** output?  That is probably one contributing factor if you see them. What happens if you put that down?

```
sudo ifconfig eth0 down
```

and then try to ping the router.  

```

ping 192.168.1.1

```

---

### Post by PolishAlice on 2007-09-22
Thanks for getting back to me so quickly.

So I fixed the ipv6 issue like you said and rebooted the computer.

Here are the commands and the output after I rebooted:
```

john@pubiodelfuego:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:F1:C8:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:CE:95:13  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1189 (1.1 KiB)  TX bytes:4894 (4.7 KiB)
          Interrupt:5 Base address:0xe000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:980 (980.0 b)  TX bytes:980 (980.0 b)
```
```

john@pubiodelfuego:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Barlow"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:46:BF:62   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=-40 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:0   Missed beacon:43

john@pubiodelfuego:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:F1:C8:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:CE:95:13  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1189 (1.1 KiB)  TX bytes:5146 (5.0 KiB)
          Interrupt:5 Base address:0xe000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1508 (1.4 KiB)  TX bytes:1508 (1.4 KiB)

```
```
john@pubiodelfuego:~$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
From 192.168.1.4 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3
``````

john@pubiodelfuego:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
``````

john@pubiodelfuego:~$ sudo ifconfig eth0 down
Password:
``````

john@pubiodelfuego:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
```

```

john@pubiodelfuego:~$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
From 192.168.1.4 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3
```

I'm interested in the whole process of troubleshooting this, so let me know if you have any good ideas.

I'm still thrown for a loop because the windows laptop can access the internet over wireless just fine.

---

### Post by noob12 on 2007-09-22
Well, you're very very close. 

You've got an association to the access point.  (I'm assuming "Barlow' is the AP that you are expecting to connect to.)  You've got an address assignment by DHCP from the access point.  So IP traffic to 192.168.1.1 had to work during that interaction.   The "Destination host unreachable" message is coming from your own interface, which generally indicates either a routing issue or a firewall.  Your routes are right, assuming 192.168.1.1 is your router.  One can see now that you have no ipv6 addresses appearing in the ifconfig, so it looks like you disabled that properly.

Do you run a firewall using iptables or firestarter or guarddog?   Can you post the output of
this command obtianed after connecting in the same way.
```

sudo iptables -nL

```

One more thing.  Let's make sure we're using an appropriate diagnostic.  When using Windows, your router does respond to pings, right?

ADDED:
Let's also look at the tail of the kernel log right after you try the pinging your router
```

ping -c 4 192.168.1.1

tail /var/log/kern.log

```

---

### Post by PolishAlice on 2007-09-22
I'm on the windows unit right

```

C:\Documents and Settings\Owner>ping 192.168.1.1

Pinging 192.168.1.1 with 32 bytes of data:

Reply from 192.168.1.1: bytes=32 time=2ms TTL=64
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64
Reply from 192.168.1.1: bytes=32 time=2ms TTL=64

Ping statistics for 192.168.1.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 2ms, Maximum = 2ms, Average = 2ms
```

---

### Post by noob12 on 2007-09-22
OK.  When you get a chance, post those diagnostics from Ubuntu...

---

### Post by PolishAlice on 2007-09-22
Allright, here is the output from the ubuntu unit

```
john@pubiodelfuego:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:F1:C8:75  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:CE:95:13  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1877 (1.8 KiB)  TX bytes:4092 (3.9 KiB)
          Interrupt:5 Base address:0x6000 Memory:e0210000-e0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

john@pubiodelfuego:~$ sudo iptables -nL
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
john@pubiodelfuego:~$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable
From 192.168.1.4 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2998ms
, pipe 3
john@pubiodelfuego:~$ tail /var/log/kern.log
Sep 22 14:33:59 pubiodelfuego kernel: [   40.049000] NET: Registered protocol family 31
Sep 22 14:33:59 pubiodelfuego kernel: [   40.049000] Bluetooth: HCI device and connection manager initialized
Sep 22 14:33:59 pubiodelfuego kernel: [   40.049000] Bluetooth: HCI socket layer initialized
Sep 22 14:34:00 pubiodelfuego kernel: [   40.137000] Bluetooth: L2CAP ver 2.8
Sep 22 14:34:00 pubiodelfuego kernel: [   40.137000] Bluetooth: L2CAP socket layer initialized
Sep 22 14:34:00 pubiodelfuego kernel: [   40.204000] Bluetooth: RFCOMM socket layer initialized
Sep 22 14:34:00 pubiodelfuego kernel: [   40.204000] Bluetooth: RFCOMM TTY layer initialized
Sep 22 14:34:00 pubiodelfuego kernel: [   40.204000] Bluetooth: RFCOMM ver 1.8
Sep 22 14:34:30 pubiodelfuego kernel: [   70.585000] NET: Registered protocol family 17
Sep 22 14:35:06 pubiodelfuego kernel: [  106.402000] ip_tables: (C) 2000-2006 Netfilter Core Team
john@pubiodelfuego:~$ 
```

I do not use a firewall to connect

Thanks again

---

### Post by deroldj on 2007-09-22
please read 
As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.

---

### Post by noob12 on 2007-09-22
deroldj:  Note that we're dealing with a wireless card here, and it's not that problem.

---

### Post by noob12 on 2007-09-22
I don't see any issue at all.  Desperation suggests power-cycling the router as well.

---

### Post by PolishAlice on 2007-09-23
OK, thanks for all the help. This box is just for casual use and it was nice to go through all of the troubleshooting steps and get a hold on what to do next time.

The wireless is router is a Netgear WGR614v6
I updated the firmware after I started having trouble,
it is very possible that it is just on the fritz

I'll go stand next to my neighbors' tonight and see if I can siphon off their connection.

If I figure anything out, I'll come back and post it here

---

