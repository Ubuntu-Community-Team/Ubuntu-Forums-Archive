---
title: "WPA-PSK network?"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by niels on 2006-08-04
Hi,

I have an ThinkPad T40p with a Intel  Intel PRO/Wireless LAN 2100 3B Mini PCI Adapter. This should work with the ipw2100 driver. I have no problem connecting to my home WEP-encrypted network, but can't connect to my fathers WPA-PSK (TKIP) encrypted network. I have tryed all the WPA options in the NetworkManager (both enterprise and personal). I haven't experienced eny problems with the familys Windows PC's.
Does anyone know why it doesn't work for me?

Niels

Ps. I don't know what the difference between the personal and the enterprice WPA is, and when I try the two WPA enterprise options, I don't know most of the parameters, and Windows doesn't ask for them.

EDIT
Here is the output from NetwoekManager when I try to connet to the network with the WPA2 personal option:
> 
niels@niels-laptop:~$ sudo NetworkManager --no-daemon
NetworkManager: <information>   starting...
NetworkManager: <WARNING>        main (): nm_data_new: Setting up dbus filter
NetworkManager: <information>   eth0: Device is fully-supported using driver 'e1 000'.
NetworkManager: <information>   nm_device_init(): waiting for device's worker th read to start
NetworkManager: <information>   nm_device_init(): device's worker thread started , continuing.
NetworkManager: <information>   Now managing wired Ethernet (802.3) device 'eth0 '.
NetworkManager: <information>   ath0: Device is fully-supported using driver 'at h_pci'.
NetworkManager: <information>   nm_device_init(): waiting for device's worker th read to start
NetworkManager: <information>   nm_device_init(): device's worker thread started , continuing.
NetworkManager: <information>   Now managing wireless (802.11) device 'ath0'.
NetworkManager: <information>   Updating allowed wireless network lists.
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <debug info>    [1154703625.226300] nm_device_802_11_wireless_get_activation _ap (): Forcing AP 'bakkensbro11'
NetworkManager: <information>   User Switch: /org/freedesktop/NetworkManager/Devices/ath0 / bakkensbro11
NetworkManager: <information>   Deactivating device ath0.
NetworkManager: <information>   Device ath0 activation scheduled...
NetworkManager: <information>   Activation (ath0) started...
NetworkManager: <information>   Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <information>   Activation (ath0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <information>   Activation (ath0) Stage 2 of 5 (Device Configure) scheduled. ..
NetworkManager: <information>   Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <information>   Activation (ath0) Stage 2 of 5 (Device Configure) starting.. .
NetworkManager: <information>   match
NetworkManager: <information>   Activation (ath0/wireless): access point 'bakkensbro11' is e ncrypted, and a key exists.  No new key needed.
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   match
NetworkManager: <information>   SUP: sending command 'INTERFACE_ADD ath0                madw ifi     /var/run/wpa_supplicant '
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'AP_SCAN 1'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ADD_NETWORK'
NetworkManager: <information>   SUP: response was '0'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 ssid 62616b6b656e7362726 f3131'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 scan_ssid 1'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 proto WPA2'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 psk <key>'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 pairwise TKIP'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'SET_NETWORK 0 group TKIP'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   SUP: sending command 'ENABLE_NETWORK 0'
NetworkManager: <information>   SUP: response was 'OK'
NetworkManager: <information>   Activation (ath0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <information>   wpa_supplicant(7330): Global control interface '/var/run/wpa _supplicant-global'
NetworkManager: <information>   wpa_supplicant(7330): RX global ctrl_iface - hexdump_ascii(l en=52):
NetworkManager: <information>   wpa_supplicant(7330):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 61 74   INTERFACE_ADD at
NetworkManager: <information>   wpa_supplicant(7330):      68 30 09 09 6d 61 64 77 69 66 69 09 2f 76 61 72   h0__madwifi_/var
NetworkManager: <information>   wpa_supplicant(7330):      2f 72 75 6e 2f 77 70 61 5f 73 75 70 70 6c 69 63   /run/wpa_supplic
NetworkManager: <information>   wpa_supplicant(7330):      61 6e 74 09                  ant_
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE GLOBAL INTERFACE_ADD 'ath0m adwifi  /var/run/wpa_supplicant '
NetworkManager: <information>   wpa_supplicant(7330): Initializing interface 'ath0' conf 'N/ A' driver 'madwifi' ctrl_interface '/var/run/wpa_supplicant'
NetworkManager: <information>   wpa_supplicant(7330): Initializing interface (2) 'ath0'
NetworkManager: <information>   wpa_supplicant(7330): EAPOL: SUPP_PAE entering state DISCONN ECTED
NetworkManager: <information>   wpa_supplicant(7330): EAPOL: KEY_RX entering state NO_KEY_RE CEIVE
NetworkManager: <information>   wpa_supplicant(7330): EAPOL: SUPP_BE entering state INITIALI ZE
NetworkManager: <information>   wpa_supplicant(7330): EAP: EAP entering state DISABLED
NetworkManager: <information>   wpa_supplicant(7330): EAPOL: External notification - portEna bled=0
NetworkManager: <information>   wpa_supplicant(7330): EAPOL: External notification - portVal id=0
NetworkManager: <information>   wpa_supplicant(7330): SIOCGIWRANGE: WE(compiled)=19 WE(sourc e)=13 enc_capa=0xf
NetworkManager: <information>   wpa_supplicant(7330):   capabilities: key_mgmt 0xf enc 0xf
NetworkManager: <information>   wpa_supplicant(7330): Own MAC address: 00:05:4e:41:a8:ed
NetworkManager: <information>   wpa_supplicant(7330): wpa_driver_madwifi_del_key: keyidx=0
NetworkManager: <information>   wpa_supplicant(7330): r_madwifi_del_key: keyidx=1
NetworkManager: <information>   wpa_supplicant(7330): wpa_driver_madwifi_del_key: keyidx=2
NetworkManager: <information>   wpa_supplicant(7330): wpa_driver_madwifi_del_key: keyidx=3
NetworkManager: <information>   wpa_supplicant(7330): wpa_driver_madwifi_set_countermeasures : enabled=0
NetworkManager: <information>   wpa_supplicant(7330): wpa_driver_madwifi_set_drop_unencrypte d: enabled=1
NetworkManager: <information>   wpa_supplicant(7330): Setting scan request: 0 sec 100000 use c
NetworkManager: <information>   wpa_supplicant(7330): Added interface ath0
NetworkManager: <information>   wpa_supplicant(7330): Wireless event: cmd=0x8b06 len=8
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=9):
NetworkManager: <information>   wpa_supplicant(7330):      41 50 5f 53 43 41 4e 20 31                  AP_SCAN 1
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=11):
NetworkManager: <information>   wpa_supplicant(7330):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE: ADD_NETWORK
NetworkManager: <information>   wpa_supplicant(7330): State: DISCONNECTED -> SCANNING
NetworkManager: <information>   wpa_supplicant(7330): Starting AP scan (broadcast SSID)
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=43):
NetworkManager: <information>   wpa_supplicant(7330):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 73   SET_NETWORK 0 ss
NetworkManager: <information>   wpa_supplicant(7330):      69 64 20 36 32 36 31 36 62 36 62 36 35 36 65 37   id 62616b6b656e7
NetworkManager: <information>   wpa_supplicant(7330):      33 36 32 37 32 36 66 33 31 33 31                  362726f3131
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE: SET_NETWORK id=0 name='ssi d' value='62616b6b656e7362726f3131'
NetworkManager: <information>   wpa_supplicant(7330): ssid - hexdump_ascii(len=12):
NetworkManager: <information>   wpa_supplicant(7330): akkensbro11
NetworkManager: <information>   wpa_supplicant(7330): Wireless event: cmd=0x8b1a len=8
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=25):
NetworkManager: <information>   wpa_supplicant(7330):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 73 63   SET_NETWORK 0 sc
NetworkManager: <information>   wpa_supplicant(7330):      61 6e 5f 73 73 69 64 20 31                  an_ssid 1
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE: SET_NETWORK id=0 name='sca n_ssid' value='1'
NetworkManager: <information>   wpa_supplicant(7330): scan_ssid=1 (0x1)
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=24):
NetworkManager: <information>   wpa_supplicant(7330):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 70 72   SET_NETWORK 0 pr
NetworkManager: <information>   wpa_supplicant(7330):      6f 74 6f 20 57 50 41 32                  oto WPA2
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE: SET_NETWORK id=0 name='pro to' value='WPA2'
NetworkManager: <information>   wpa_supplicant(7330): proto: 0x2
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=30):
NetworkManager: <information>   wpa_supplicant(7330):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 6b 65   SET_NETWORK 0 ke
NetworkManager: <information>   wpa_supplicant(7330):      79 5f 6d 67 6d 74 20 57 50 41 2d 50 53 4b         y_mgmt WPA-PSK
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE: SET_NETWORK id=0 name='key _mgmt' value='WPA-PSK'
NetworkManager: <information>   wpa_supplicant(7330): key_mgmt: 0x2
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=82):  [REMOVED]
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE: SET_NETWORK id=0 name='psk ' value='6707cfbce73bb48cc8327cd1bb14255bc8633823195ec2a7631277e7ae1d954d'
NetworkManager: <information>   wpa_supplicant(7330): PSK - hexdump(len=32): [REMOVED]
NetworkManager: <information>   wpa_supplicant(7330):  hexdump_ascii(len=27):
NetworkManager: <information>   wpa_supplicant(7330):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 70 61   SET_NETWORK 0 pa
NetworkManager: <information>   wpa_supplicant(7330):      69 72 77 69 73 65 20 54 4b 49 50                  irwise TKIP
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE: SET_NETWORK id=0 name='pai rwise' value='TKIP'
NetworkManager: <information>   wpa_supplicant(7330): pairwise: 0x8
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=24):
NetworkManager: <information>   wpa_supplicant(7330):      53 45 54 5f 4e 45 54 57 4f 52 4b 20 30 20 67 72   SET_NETWORK 0 gr
NetworkManager: <information>   wpa_supplicant(7330):      6f 75 70 20 54 4b 49 50                  oup TKIP
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE: SET_NETWORK id=0 name='gro up' value='TKIP'
NetworkManager: <information>   wpa_supplicant(7330): group: 0x8
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=16):
NetworkManager: <information>   wpa_supplicant(7330):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0
NetworkManager: <information>   wpa_supplicant(7330): CTRL_IFACE: ENABLE_NETWORK id=0
NetworkManager: <information>   wpa_supplicant(7330): Setting scan request: 0 sec 0 usec
NetworkManager: <information>   wpa_supplicant(7330): Starting AP scan (specific SSID)
NetworkManager: <information>   wpa_supplicant(7330): Scan SSID - hexdump_ascii(len=12):
NetworkManager: <information>   wpa_supplicant(7330):      62 61 6b 6b 65 6e 73 62 72 6f 31 31               bakkensbro11
NetworkManager: <information>   wpa_supplicant(7330): RX ctrl_iface - hexdump_ascii(len=6):
NetworkManager: <information>   wpa_supplicant(7330):      41 54 54 41 43 48                  ATTACH
NetworkManager: <information>   Activation (ath0/wireless): association took too long (>120s), failing activation.
NetworkManager: <information>   Activation (ath0) failure scheduled...
NetworkManager: <information>   Activation (ath0) failed for access point (bakkensbro11)
NetworkManager: <information>   Activation (ath0) failed.
NetworkManager: <information>   Deactivating device ath0.
NetworkManager: <information>   match
NetworkManager: <WARNING>        nm_signal_handler (): Caught signal 2, shutting down normally.
NetworkManager: <information>   Caught terminiation signal
NetworkManager: <debug info>    [1154703784.410682] nm_print_open_socks (): Open Sockets List:
NetworkManager: <debug info>    [1154703784.410760] nm_print_open_socks (): Open Sockets List Done.
NetworkManager: <information>   Deactivating device eth0.
NetworkManager: <information>   Deactivating device ath0.
niels@niels-laptop:~$


---

