---
title: "Syslog output"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by l951b951 on 2007-01-31
Hi guys,  I've been having some problems with my wireless card, I'm trying to troubleshoot whether it is a flaky driver or hardware.  I have my syslog viewer open in desktop 4 so I can see my problems when they happen.  However, right now (with internet working) I'm getting this output.  It looks, to me, that my wlan0 is sleeping, but I'm posting on it right now.  What does this mean?

> Jan 31 12:54:29 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jan 31 12:54:33 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan 31 12:54:41 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jan 31 12:54:55 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan 31 12:55:08 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan 31 12:55:22 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan 31 12:55:29 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Jan 31 12:55:30 localhost dhclient: No DHCPOFFERS received.
Jan 31 12:55:30 localhost dhclient: No working leases in persistent database - sleeping.
Jan 31 13:02:19 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Jan 31 13:02:25 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan 31 13:02:39 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan 31 13:02:46 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Jan 31 13:03:06 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Jan 31 13:03:20 localhost dhclient: No DHCPOFFERS received.
Jan 31 13:03:20 localhost dhclient: No working leases in persistent database - sleeping.

---

### Post by l951b951 on 2007-01-31
while posting, my syslog got busy again.  However, my internet is still working.


> Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): tor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 33 31 38 2d 31 00 30 00 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Cancelling scan request 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): WPA: clearing own WPA/RSN IE 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Automatic auth_alg selection: 0x1 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): WPA: clearing AP WPA IE 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): WPA: clearing AP RSN IE 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): WPA: clearing own WPA/RSN IE 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): No keys have been configured - skip key clearing 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=1 seq_len=0 key_len=13 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): wpa_driver_wext_set_drop_unencrypted 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): State: SCANNING -> ASSOCIATING 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): wpa_driver_wext_associate 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Association request to the driver failed 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 33 31 38 2d 31 00 30 00 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Setting authentication timeout: 5 sec 0 usec 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: External notification - portControl=ForceAuthorized 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Wireless event: cmd=0x8b2a len=8 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Wireless event: cmd=0x8b2a len=8 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Wireless event: cmd=0x8b06 len=8 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): cmd=0x8b15 len=20 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Wireless event: new AP: 00:00:00:00:00:00 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Added BSSID 00:00:00:00:00:00 into blacklist 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): State: ASSOCIATING -> DISCONNECTED 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: External notification - portEnabled=0 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: External notification - portValid=0 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 33 31 38 2d 31 00 30 00 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Wireless event: cmd=0x8b1a len=18 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Wireless event: cmd=0x8b15 len=20 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Wireless event: new AP: 00:00:00:00:00:00 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): BSSID 00:00:00:00:00:00 blacklist count incremented to 2 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): State: DISCONNECTED -> DISCONNECTED 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: External notification - portEnabled=0 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: External notification - portValid=0 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 33 31 38 2d 31 00 30 00 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Wireless event: cmd=0x8b15 len=20 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): w AP: 00:0f:cc:68:70:d0 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): State: DISCONNECTED -> ASSOCIATED 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Associated to a new BSS: BSSID=00:0f:cc:68:70:d0 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Associated with 00:0f:cc:68:70:d0 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 33 31 38 2d 31 00 30 00 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): WPA: Association event - clear replay counter 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: External notification - portEnabled=0 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: External notification - portValid=0 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: External notification - portEnabled=1 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: SUPP_PAE entering state S_FORCE_AUTH 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): EAPOL: SUPP_BE entering state IDLE 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): Cancelling authentication timeout 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): State: ASSOCIATED -> COMPLETED 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): CTRL-EVENT-CONNECTED - Connection to 00:0f:cc:68:70:d0 completed (auth) 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): CTRL_IFACE monitor send - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 33 31 38 2d 31 00 30 00 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added 
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329):  
Jan 31 13:06:19 localhost NetworkManager: <information>^Iwpa_supplicant(5329): RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added 
Jan 31 13:06:19 localhost last message repeated 19 times

---

### Post by Brunellus on 2007-01-31
you're getting no dhcp offers for your dhcp requests.  fault is upstream with the dhcp server, my guess. (not a good one though)

moving to a more competent forum.

---

### Post by l951b951 on 2007-01-31
Appreciate the move.  I figured out that hte DHCP offers are for my eth0 (nic) which isn't plugged in.  My wlan0 was working.
However, my connection just died.  Here is the output at the death of it.  Can anyone tell if it is a bad driver or if it is a card malfunction?  


> Jan 31 13:54:56 localhost kernel: [17183683.288000] NETDEV WATCHDOG: wlan0: transmit timed out
Jan 31 13:54:56 localhost kernel: [17183683.296000] rtl8180: Bringing up iface
Jan 31 13:54:56 localhost kernel: [17183683.504000] rtl8180: Card successfully reset
Jan 31 13:55:04 localhost NetworkManager: <information>^Iwlan0: link timed out. 
Jan 31 13:55:04 localhost NetworkManager: <information>^ISWITCH: found better connection 'wlan0/3207 7434' than current connection 'wlan0/3207 7434'.  same_ssid=1, have_link=0 
Jan 31 13:55:04 localhost NetworkManager: <information>^IWill activate connection 'wlan0/3207 7434'. 
Jan 31 13:55:04 localhost NetworkManager: <information>^IDevice wlan0 activation scheduled... 
Jan 31 13:55:04 localhost NetworkManager: <information>^Imatch 
Jan 31 13:55:04 localhost NetworkManager: <information>^IDeactivating device wlan0. 
Jan 31 13:55:04 localhost dhclient: DHCPRELEASE on wlan0 to 192.168.1.254 port 67
Jan 31 13:55:05 localhost kernel: [17183692.920000] rtl8180: Setting SW wep key
Jan 31 13:55:05 localhost last message repeated 3 times
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) started... 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 31 13:55:09 localhost NetworkManager: <information>^Imatch 
Jan 31 13:55:09 localhost NetworkManager: <information>^Imatch 
Jan 31 13:55:09 localhost NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface wlan0 
Jan 31 13:55:09 localhost NetworkManager: <information>^IDHCP daemon state is now 11 (unknown) for interface wlan0 
Jan 31 13:55:09 localhost NetworkManager: <information>^IDHCP daemon state is now 14 (normal exit) for interface wlan0 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan 31 13:55:09 localhost kernel: [17183695.100000] rtl8180: Setting SW wep key
Jan 31 13:55:09 localhost NetworkManager: <information>^Imatch 
Jan 31 13:55:09 localhost kernel: [17183695.108000] rtl8180: Bringing up iface
Jan 31 13:55:09 localhost NetworkManager: <information>^Imatch 
Jan 31 13:55:09 localhost kernel: [17183695.532000] rtl8180: Card successfully reset
Jan 31 13:55:09 localhost NetworkManager: <information>^Imatch 
Jan 31 13:55:09 localhost kernel: [17183696.552000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 31 13:55:09 localhost NetworkManager: <information>^Imatch 
Jan 31 13:55:09 localhost last message repeated 9 times
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0/wireless): access point '3207 7434' is encrypted, but NO valid key exists.  New key needed. 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) New wireless user key requested for network '3207 7434'. 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) New wireless user key for network '3207 7434' received. 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan 31 13:55:09 localhost NetworkManager: <information>^IActivation (wlan0/wireless): access point '3207 7434' is encrypted, and a key exists.  No new key needed. 
Jan 31 13:55:09 localhost NetworkManager: <information>^Imatch 
Jan 31 13:55:09 localhost NetworkManager: <information>^Imatch 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant^I' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: response was '0' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 333230372037343334' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Jan 31 13:55:10 localhost kernel: [17183697.852000] rtl8180: Setting SW wep key
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jan 31 13:55:10 localhost kernel: [17183697.852000] rtl8180: Setting SW wep key
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Jan 31 13:55:10 localhost kernel: [17183697.852000] rtl8180: Setting SW wep key
Jan 31 13:55:10 localhost NetworkManager: <information>^ISUP: response was 'OK' 
Jan 31 13:55:10 localhost kernel: [17183697.852000] rtl8180: Setting SW wep key
Jan 31 13:55:10 localhost NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Global control interface '/var/run/wpa_supplicant-global' 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): RX global ctrl_iface - hexdump_ascii(len=50): 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 77 6c   INTERFACE_ADD wl 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      61 6e 30 09 09 77 65 78 74 09 2f 76 61 72 2f 72   an0__wext_/var/r 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      75 6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e   un/wpa_supplican 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      74 09                                             t_               
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): CTRL_IFACE GLOBAL INTERFACE_ADD 'wlan0^I^Iwext^I/var/run/wpa_supplicant^I' 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Initializing interface 'wlan0' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Initializing interface (2) 'wlan0' 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): EAPOL: SUPP_PAE entering state DISCONNECTED 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): EAPOL: SUPP_BE entering state INITIALIZE 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): EAP: EAP entering state DISABLED 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): EAPOL: External notification - portEnabled=0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): EAPOL: External notification - portValid=0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): SIOCGIWRANGE: WE(compiled)=19 WE(source)=16 enc_capa=0x0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):   capabilities: key_mgmt 0x0 enc 0x3 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Own MAC address: 00:09:5b:63:40:6a 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): wpa_driver_wext_set_wpa 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): PA. 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): wpa_driver_wext_set_countermeasures 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): wpa_driver_wext_set_drop_unencrypted 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Setting scan request: 0 sec 100000 usec 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Added interface wlan0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Wireless event: cmd=0x8b06 len=8 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): RX ctrl_iface - hexdump_ascii(len=9): 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Wireless event: cmd=0x8b2a len=8 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): RX ctrl_iface - hexdump_ascii(len=11): 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): CTRL_IFACE: ADD_NETWORK 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Wireless event: cmd=0x8b2a len=8 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): e - hexdump_ascii(len=37): 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      69 64 20 33 33 33 32 33 30 33 37 32 30 33 37 33   id 3332303720373 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      34 33 33 33 34                                    43334            
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): CTRL_IFACE: SET_NETWORK id=0 name='ssid' value='333230372037343334' 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): ssid - hexdump_ascii(len=9): 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      33 32 30 37 20 37 34 33 34                        3207 7434        
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Wireless event: cmd=0x8b2a len=8 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): RX ctrl_iface - hexdump_ascii(len=27): 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      79 5f 6d 67 6d 74 20 4e 4f 4e 45                  y_mgmt NONE      
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' value='NONE' 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): key_mgmt: 0x4 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Wireless event: cmd=0x8b2a len=8 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): RX ctrl_iface - hexdump_ascii(len=49): [REMOVED] 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): CTRL_IFACE: SET_NETWORK id=0 name='wep_key0' value='[REMOVED]' 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): wep_key0 - hexdump(len=13): [REMOVED] 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): RX ctrl_iface - hexdump_ascii(len=29): 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 77 65   SET_NETWORK 0 we 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): 69 64 78 20 30            p_tx_keyidx 0    
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): CTRL_IFACE: SET_NETWORK id=0 name='wep_tx_keyidx' value='0' 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): wep_tx_keyidx=0 (0x0) 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): RX ctrl_iface - hexdump_ascii(len=16): 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): CTRL_IFACE: ENABLE_NETWORK id=0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Setting scan request: 0 sec 0 usec 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): State: DISCONNECTED -> SCANNING 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Starting AP scan (broadcast SSID) 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): RX ctrl_iface - hexdump_ascii(len=6): 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820):      41 54 54 41 43 48                                 ATTACH           
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): CTRL_IFACE monitor attached - hexdump(len=42): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 33 31 38 2d 33 00 30 00 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Scan timeout - try to get results 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Received 0 bytes of scan results (0 BSSes) 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Scan results: 0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Selecting BSS from priority group 0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): No suitable AP found. 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Setting scan request: 5 sec 0 usec 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Starting AP scan (broadcast SSID) 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Scan timeout - try to get results 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Received 0 bytes of scan results (0 BSSes) 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Scan results: 0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): Selecting BSS from priority group 0 
Jan 31 13:55:21 localhost NetworkManager: <information>^Iwpa_supplicant(9820): No suitable AP found. 


To get my connection to work again I rightclick my network manager applet icon and disable wireless, physically eject my pcmia card, put it back in, and enable wireless.  It works until the next time it dies.

---

### Post by l951b951 on 2007-02-01
I'm still trying to work this out, so I'm trying to rephrase the question.

For my wireless card I installed the rtl8180 driver with the ndiswrapper.  In the following portion of the output, the part that says "localhost kernel" is that card reset being done by the driver, the kernel, or hardware?  I'm not sure whether "localhost kernel" is the entity resetting the card or just reporting that it was reset.
Is there anyway to tell?


> Jan 31 13:54:56 localhost kernel: [17183683.288000] NETDEV WATCHDOG: wlan0: transmit timed out
Jan 31 13:54:56 localhost kernel: [17183683.296000] rtl8180: Bringing up iface
Jan 31 13:54:56 localhost kernel: [17183683.504000] rtl8180: Card successfully reset

---

