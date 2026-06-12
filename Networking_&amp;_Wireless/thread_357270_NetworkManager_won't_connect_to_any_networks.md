---
title: "NetworkManager won't connect to any networks"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by thoughts on 2007-02-09
I've got NetworkManager installed on a new Edgy install.  I have an Intel 2200BG built-in wireless card.

When I click the NetworkManager icon, I can see the wireless networks around me.  But when I try to connect to them, it always fails.  One of them is my own WPA-encrypted router, and another one is an open router with a strong signal.

When I try to connect, the NetworkManager icon changes to a blue fireball spinning in a circle with 2 big dots on it.  Sometimes the 2 dots are gray, and sometimes they're green.  But in either case, the blue fireball just spins for a while and then it switches back to the "no connection" icon.

Why would NetworkManager be able to see networks but not connect to any of them?

And is it possible to use command-line stuff to try and connect?  If so, which commands should I use (for my WPA router and/or for an open router)?  There are tons of different examples given around here, but some of the instructions I've read have said that you can't use other wireless tools while using NetworkManager.

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by Tuffy on 2007-02-09
I have the exact same problem :(

---

### Post by spd106 on 2007-02-09
First I suggest that you check that you are entering the correct key. 

If you are certain that is not the problem then perhaps check the /var/log/syslog file for any errors. This can be done easily through System-> Admin -> System Log. If it starts up blank then you need to open the above file.

---

### Post by thoughts on 2007-02-09
I've entered the key many times now, and verified it on other systems.

I've captured 2 minutes' worth of syslog activity that's ~solely from NetworkManager, but it's ~300k of data.  It looks like the *.txt file attachment feature on this forum is limited to 20k, so... here are some snippets instead:

```

NetworkManager: <information>^Istarting... 
NetworkManager: <information>^Ieth1: Device is fully-supported using driver 'ipw2200'. 
NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
NetworkManager: <information>^INow managing wireless (802.11) device 'eth1'. 
NetworkManager: <information>^IDeactivating device eth1. 
hcid[4276]: Register path:/org/bluez fallback:1
NetworkManager: <information>^IUpdating allowed wireless network lists. 
NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth1'. 
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
NetworkManager: <information>^IWill activate connection 'eth1/myapname'. 
NetworkManager: <information>^IDevice eth1 activation scheduled... 
NetworkManager: <information>^IActivation (eth1) started... 
NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
NetworkManager: <information>^IActivation (eth1/wireless): access point 'myapname' is encrypted, but NO valid key exists.  New key needed. 
NetworkManager: <information>^IActivation (eth1) New wireless user key requested for network 'myapname'. 
NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
kernel: [17190991.964000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
kernel: [17191002.564000] eth1: no IPv6 routers present
NetworkManager: <information>^IActivation (eth1) New wireless user key for network 'myapname' received. 
NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
NetworkManager: <information>^IActivation (eth1/wireless): access point 'myapname' is encrypted, and a key exists.  No new key needed. 
NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
NetworkManager: <information>^ISUP: response was 'OK' 
NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
NetworkManager: <information>^ISUP: response was 'OK' 
NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
NetworkManager: <information>^ISUP: response was '0' 
NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 636c616e616c6c656e6c616e' 
NetworkManager: <information>^ISUP: response was 'OK' 
NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 proto WPA' 
NetworkManager: <information>^ISUP: response was 'OK' 
NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
NetworkManager: <information>^ISUP: response was 'OK' 
NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 psk <key>' 
NetworkManager: <information>^ISUP: response was 'OK' 
NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
NetworkManager: <information>^ISUP: response was 'OK' 
NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
NetworkManager: <information>^Iwpa_supplicant(11664): Global control interface '/var/run/wpa_supplicant-global' 
NetworkManager: <information>^Iwpa_supplicant(11664): RX global ctrl_iface - hexdump_ascii(len=49): 
NetworkManager: <information>^Iwpa_supplicant(11664):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 65 74   INTERFACE_ADD et 
NetworkManager: <information>^Iwpa_supplicant(11664):      68 31 09 09 77 65 78 74 09 2f 76 61 72 2f 72 75   h1__wext_/var/ru 
NetworkManager: <information>^Iwpa_supplicant(11664):      6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e 74   n/wpa_supplicant 
NetworkManager: <information>^Iwpa_supplicant(11664):      09                                                _                
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE GLOBAL INTERFACE_ADD 'eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
NetworkManager: <information>^Iwpa_supplicant(11664): Initializing interface 'eth1' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' bridge 'N/A' 
NetworkManager: <information>^Iwpa_supplicant(11664): Initializing interface (2) 'eth1' 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: SUPP_PAE entering state DISCONNECTED 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: SUPP_BE entering state INITIALIZE 
NetworkManager: <information>^Iwpa_supplicant(11664): EAP: EAP entering state DISABLED 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: External notification - portEnabled=0 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: External notification - portValid=0 
NetworkManager: <information>^Iwpa_supplicant(11664): SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf 
NetworkManager: <information>^Iwpa_supplicant(11664):   capabilities: key_mgmt 0xf enc 0xf 
NetworkManager: <information>^Iwpa_supplicant(11664): WEXT: Operstate: linkmode=1, operstate=5 
NetworkManager: <information>^Iwpa_supplicant(11664): 5 
NetworkManager: <information>^Iwpa_supplicant(11664): wpa_driver_wext_set_wpa 
NetworkManager: <information>^Iwpa_supplicant(11664): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
NetworkManager: <information>^Iwpa_supplicant(11664): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
NetworkManager: <information>^Iwpa_supplicant(11664): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
NetworkManager: <information>^Iwpa_supplicant(11664): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
NetworkManager: <information>^Iwpa_supplicant(11664): wpa_driver_wext_set_countermeasures 
NetworkManager: <information>^Iwpa_supplicant(11664): wpa_driver_wext_set_drop_unencrypted 
NetworkManager: <information>^Iwpa_supplicant(11664): Setting scan request: 0 sec 100000 usec 
NetworkManager: <information>^Iwpa_supplicant(11664): Added interface eth1 
NetworkManager: <information>^Iwpa_supplicant(11664): Wireless event: cmd=0x8b06 len=8 
NetworkManager: <information>^Iwpa_supplicant(11664): RX ctrl_iface - hexdump_ascii(len=9): 
NetworkManager: <information>^Iwpa_supplicant(11664):      41 50 5f 53 43 41 4e 20 31                        AP_SCAN 1        
NetworkManager: <information>^Iwpa_supplicant(11664): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
NetworkManager: <information>^Iwpa_supplicant(11664): RX ctrl_iface - hexdump_ascii(len=11): 
NetworkManager: <information>^Iwpa_supplicant(11664):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: ADD_NETWORK 
NetworkManager: <information>^Iwpa_supplicant(11664): RX ctrl_iface - hexdump_ascii(len=43): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: SET_NETWORK id=0 name='ssid' 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: value - hexdump_ascii(len=24): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): ssid - hexdump_ascii(len=12): 
NetworkManager: <information>^Iwpa_supplicant(11664):      63 6c 61 6e 61 6c 6c 65 6e 6c 61 6e               myapname     
NetworkManager: <information>^Iwpa_supplicant(11664): ce - hexdump_ascii(len=23): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: SET_NETWORK id=0 name='proto' 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: value - hexdump_ascii(len=3): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): proto: 0x1 
NetworkManager: <information>^Iwpa_supplicant(11664): RX ctrl_iface - hexdump_ascii(len=30): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: value - hexdump_ascii(len=7): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): key_mgmt: 0x2 
NetworkManager: <information>^Iwpa_supplicant(11664): RX ctrl_iface - hexdump_ascii(len=82): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: SET_NETWORK id=0 name='psk' 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: value - hexdump_ascii(len=64): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): PSK - hexdump(len=32): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): RX ctrl_iface - hexdump_ascii(len=16): 
NetworkManager: <information>^Iwpa_supplicant(11664):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL_IFACE: ENABLE_NETWORK id=0 
NetworkManager: <information>^Iwpa_supplicant(11664): Setting scan request: 0 sec 0 usec 
NetworkManager: <information>^Iwpa_supplicant(11664): State: DISCONNECTED -> SCANNING 
NetworkManager: <information>^Iwpa_supplicant(11664): Starting AP scan (broadcast SSID) 
NetworkManager: <information>^Iwpa_supplicant(11664): Trying to get current scan results first without requesting a new scan to speed up initial association 
NetworkManager: <information>^Iwpa_supplicant(11664): Received 709 bytes of scan results (3 BSSes) 
NetworkManager: <information>^Iwpa_supplicant(11664): Scan results: 3 
NetworkManager: <information>^Iwpa_supplicant(11664): Selecting BSS from priority group 0 
NetworkManager: <information>^Iwpa_supplicant(11664): 0: 00:90:4c:7e:00:64 ssid='myapname' wpa_ie_len=24 rsn_ie_len=0 caps=0x11 
NetworkManager: <information>^Iwpa_supplicant(11664): A IE 
NetworkManager: <information>^Iwpa_supplicant(11664): Trying to associate with 00:90:4c:7e:00:64 (SSID='myapname' freq=0 MHz) 
NetworkManager: <information>^Iwpa_supplicant(11664): Cancelling scan request 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: clearing own WPA/RSN IE 
NetworkManager: <information>^Iwpa_supplicant(11664): Automatic auth_alg selection: 0x1 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: using IEEE 802.11i/D3.0 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: clearing AP RSN IE 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: using GTK TKIP 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: using PTK TKIP 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: using KEY_MGMT WPA-PSK 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
NetworkManager: <information>^Iwpa_supplicant(11664): No keys have been configured - skip key clearing 
NetworkManager: <information>^Iwpa_supplicant(11664): wpa_driver_wext_set_drop_unencrypted 
NetworkManager: <information>^Iwpa_supplicant(11664): State: SCANNING -> ASSOCIATING 
NetworkManager: <information>^Iwpa_supplicant(11664): WEXT: Operstate: linkmode=-1, operstate=5 
NetworkManager: <information>^Iwpa_supplicant(11664): wpa_driver_wext_associate 
NetworkManager: <information>^Iwpa_supplicant(11664): Setting authentication timeout: 10 sec 0 usec 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: External notification - EAP success=0 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: External notification - EAP fail=0 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: External notification - portControl=Auto 
NetworkManager: <information>^Iwpa_supplicant(11664): 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 31 31 36 30 32 2d 31 00 
NetworkManager: <information>^Iwpa_supplicant(11664): Wireless event: cmd=0x8b06 len=8 
NetworkManager: <information>^Iwpa_supplicant(11664): Wireless event: cmd=0x8b1a len=21 
NetworkManager: <information>^Iwpa_supplicant(11664): Wireless event: cmd=0x8b15 len=20 
NetworkManager: <information>^Iwpa_supplicant(11664): Wireless event: new AP: 00:00:00:00:00:00 
NetworkManager: <information>^Iwpa_supplicant(11664): Added BSSID 00:90:4c:7e:00:64 into blacklist 
NetworkManager: <information>^Iwpa_supplicant(11664): State: ASSOCIATING -> DISCONNECTED 
NetworkManager: <information>^Iwpa_supplicant(11664): WEXT: Operstate: linkmode=-1, operstate=5 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: External notification - portEnabled=0 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: External notification - portValid=0 
NetworkManager: <information>^Iwpa_supplicant(11664): EAPOL: External notification - EAP success=0 
NetworkManager: <information>^Iwpa_supplicant(11664): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 

[snip]

NetworkManager: <information>^Iwpa_supplicant(11664): IEEE 802.1X RX: version=1 type=3 length=95 
NetworkManager: <information>^Iwpa_supplicant(11664):   EAPOL-Key type=254 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack) 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_length=32 key_data_length=0 
NetworkManager: <information>^Iwpa_supplicant(11664):   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):  hexdump(len=32): 4c 61 7d 36 42 f0 f4 76 63 ce 50 49 d9 8a 29 bf c1 03 b2 48 c0 e1 a9 08 1d 01 9c 20 82 b4 72 9f 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 4c 61 7d 36 42 f0 f4 76 63 ce 50 49 d9 8a 29 bf c1 03 b2 48 c0 e1 a9 08 1d 01 9c 20 82 b4 72 9f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664): State: ASSOCIATED -> 4WAY_HANDSHAKE 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: RX message 1 of 4-Way Handshake from 00:90:4c:7e:00:64 (ver=1) 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: Renewed SNonce - hexdump(len=32): 33 e7 08 bc 77 7b 9d a2 1a 86 23 c7 cf 2a 0a 80 a1 d9 0c ba 03 33 7d 4f 0b f0 38 1b f6 30 90 ba 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: PMK - hexdump(len=32): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): MOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: Sending EAPOL-Key 2/4 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 00 33 e7 08 bc 77 7b 9d a2 1a 86 23 c7 cf 2a 0a 80 a1 d9 0c ba 03 33 7d 4f 0b f0 38 1b f6 30 90 ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 d6 9f 48 17 c7 e8 3e f0 41 6f 8d d6 61 4e 23 53 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
NetworkManager: <information>^Iwpa_supplicant(11664): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
NetworkManager: <information>^Iwpa_supplicant(11664): RX EAPOL from 00:90:4c:7e:00:64 
NetworkManager: <information>^Iwpa_supplicant(11664): RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 4c 61 7d 36 42 f0 f4 76 63 ce 50 49 d9 8a 29 bf c1 03 b2 48 c0 e1 a9 08 1d 01 9c 20 82 b4 72 9f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664): IEEE 802.1X RX: version=1 type=3 length=95 
NetworkManager: <information>^Iwpa_supplicant(11664): 54 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack) 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_length=32 key_data_length=0 
NetworkManager: <information>^Iwpa_supplicant(11664):   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_nonce - hexdump(len=32): 4c 61 7d 36 42 f0 f4 76 63 ce 50 49 d9 8a 29 bf c1 03 b2 48 c0 e1 a9 08 1d 01 9c 20 82 b4 72 9f 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 4c 61 7d 36 42 f0 f4 76 63 ce 50 49 d9 8a 29 bf c1 03 b2 48 c0 e1 a9 08 1d 01 9c 20 82 b4 72 9f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664): State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: RX message 1 of 4-Way Handshake from 00:90:4c:7e:00:64 (ver=1) 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: PMK - hexdump(len=32): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: PTK - hexdump(len=64): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: Sending EAPOL-Key 2/4 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 33 e7 08 bc 77 7b 9d a2 1a 86 23 c7 cf 2a 0a 80 a1 d9 0c ba 03 33 7d 4f 0b f0 38 1b f6 30 90 ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b0 2d 50 3a 2c 39 6f 1a 29 b8 73 8d 82 8d 1c 26 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 
NetworkManager: <information>^Iwpa_supplicant(11664): RX EAPOL from 00:90:4c:7e:00:64 
NetworkManager: <information>^Iwpa_supplicant(11664): RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 02 4c 61 7d 36 42 f0 f4 76 63 ce 50 49 d9 8a 29 bf c1 03 b2 48 c0 e1 a9 08 1d 01 9c 20 82 b4 72 9f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664): IEEE 802.1X RX: version=1 type=3 length=95 
NetworkManager: <information>^Iwpa_supplicant(11664):   EAPOL-Key type=254 
NetworkManager: <information>^Iwpa_supplicant(11664):  (ver=1 keyidx=0 rsvd=0 Pairwise Ack) 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_length=32 key_data_length=0 
NetworkManager: <information>^Iwpa_supplicant(11664):   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_nonce - hexdump(len=32): 4c 61 7d 36 42 f0 f4 76 63 ce 50 49 d9 8a 29 bf c1 03 b2 48 c0 e1 a9 08 1d 01 9c 20 82 b4 72 9f 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664):   key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 02 4c 61 7d 36 42 f0 f4 76 63 ce 50 49 d9 8a 29 bf c1 03 b2 48 c0 e1 a9 08 1d 01 9c 20 82 b4 72 9f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
NetworkManager: <information>^Iwpa_supplicant(11664): State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: RX message 1 of 4-Way Handshake from 00:90:4c:7e:00:64 (ver=1) 
NetworkManager: <information>^Iwpa_supplicant(11664): WPA: PMK - hexdump(len=32): [REMOVED] 
NetworkManager: <information>^Iwpa_supplicant(11664): (len=64): [REMOVED] 
NetworkManager: <information>^IActivation (eth1/wireless): association took too long (>60s), failing activation. 
NetworkManager: <information>^IActivation (eth1) failure scheduled... 
NetworkManager: <information>^IActivation (eth1) failed for access point (myapname) 
NetworkManager: <information>^IActivation (eth1) failed. 
NetworkManager: <information>^IDeactivating device eth1. 
dhclient: receive_packet failed on eth1: Network is down
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
dhclient: send_packet: Network is down
dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
kernel: [17191090.576000] eth1: no IPv6 routers present
dhclient: No DHCPOFFERS received.
dhclient: No working leases in persistent database - sleeping.

```

The stuff that I've omitted in the middle looked like the same output over and over and over.

You can see near the top that it accepted my key, but then below that it seems to indicate that the key length is zero?

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by spd106 on 2007-02-09
Is your AP set to broadcast it's ssid. I know Network Manager often has trouble finding and connecting to APs that don't. Particularly if it hasn't connected to the AP before.

I had this or a similar issue with NM before on my PC. I the end I gave up and just used wpa_supplicant directly. Roaming isn't an issue since it's a desktop. The best guide I used is linked in my sig, there's also the wireless forum sticky on WPA.

You might also want to have a look at this page for more information on NM [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

---

### Post by thoughts on 2007-02-10
This issue is fixed for me!!

Looks like it was partly user error and partly Windows error.  The WPA key that I was trying to use, and that I tested on a different system running Windows XP, was incorrect by one character.  But for some reason, the XP system still connected to the router for a few hours after I entered the incorrect key.  But then tonight, suddenly it stopped connecting.  I entered the password and it wouldn't accept it, so I changed that one character and it worked again.  So I tried the different password on Edgy and it worked too!

I still can't connect to the open router that I mentioned, but that only has about 40% signal strength, so maybe that's the issue there.

One other thing to note: once it connected, the Edgy system would drop the connection exactly every 10 seconds for about 1 second.  The wifi LED would briefly flash out, the NetworkManager signal icon would briefly go to zero, and my mouse would stop responding in my VNC window.  But just for about 1 second; it would then come right back, and the VNC window for example didn't even disconnect/close.  And exactly 10 seconds later, it happened again... over and over.  Rebooting fixed this problem.

Anyway, I now have working wifi under Ubuntu for the first time, with a sweet little applet (NetworkManager) that lets me easily switch networks AND which supports WPA.  I'm very happy.

Thanks to everyone who posted here.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

