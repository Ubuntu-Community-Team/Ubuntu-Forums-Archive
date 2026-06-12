---
title: "Connecting to ad-hoc mesh using olsrd"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by st0nes on 2007-09-05
Good day (or night),

I am running Ubuntu Feisty with kernel 2.6.22-9 experiencing difficulty connecting to an ad-hoc community wireless mesh using olsrd.  olsrd "sees" the network, but will not allow me to connect.  Here is an extract from /var/log/syslog:-
```
Sep  4 18:29:12 mark-laptop NetworkManager: <information>^Istarting... 
Sep  4 18:29:30 mark-laptop NetworkManager: <information>^INow managing wireless (802.11) device 'wlan0'. 
Sep  4 18:29:30 mark-laptop NetworkManager: <information>^IDeactivating device wlan0. 
Sep  4 18:30:21 mark-laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Sep  4 18:31:46 mark-laptop NetworkManager: <debug info>^I[1188923506.426376] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial'). 
Sep  4 18:31:46 mark-laptop NetworkManager: <debug info>^I[1188923506.941139] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0'). 
Sep  4 18:31:47 mark-laptop NetworkManager: <debug info>^I[1188923507.037149] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_usbraw'). 
Sep  4 18:31:47 mark-laptop NetworkManager: <debug info>^I[1188923507.236833] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c016_noserial_if0_logicaldev_input'). 
Sep  4 18:32:00 mark-laptop NetworkManager: <debug info>^I[1188923520.868814] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'communimesh' 
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / communimesh 
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IDeactivating device wlan0. 
Sep  4 18:32:00 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IDevice wlan0 activation scheduled... 
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IActivation (wlan0) started... 
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Sep  4 18:32:00 mark-laptop NetworkManager: <information>^IActivation (wlan0/wireless): access point 'communimesh' is unencrypted, no key needed. 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant^I' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: sending command 'AP_SCAN 2' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: response was '0' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 636f6d6d756e696d657368' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 mode 1' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^ISUP: response was 'OK' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Global control interface '/var/run/wpa_supplicant-global' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RX global ctrl_iface - hexdump_ascii(len=50): 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273):      49 4e 54 45 52 46 41 43 45 5f 41 44 44 20 77 6c   INTERFACE_ADD wl 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273):      61 6e 30 09 09 77 65 78 74 09 2f 76 61 72 2f 72   an0__wext_/var/r 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273):      75 6e 2f 77 70 61 5f 73 75 70 70 6c 69 63 61 6e   un/wpa_supplican 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273):      74 09                                             t_               
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE GLOBAL INTERFACE_ADD 'wlan0^I^Iwext^I/var/run/wpa_supplicant^I' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Initializing interface 'wlan0' conf 'N/A' driver 'wext' ctrl_interface '/var/run/wpa_supplicant' bridge 'N/A' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Initializing interface (2) 'wlan0' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAPOL: SUPP_PAE entering state DISCONNECTED 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAPOL: KEY_RX entering state NO_KEY_RECEIVE 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAPOL: SUPP_BE entering state INITIALIZE 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAP: EAP entering state DISABLED 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAPOL: External notification - portEnabled=0 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAPOL: External notification - portValid=0 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273):   capabilities: key_mgmt 0xf enc 0xf 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WEXT: Operstate: linkmode=1, operstate=5 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): f:4c 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_wpa 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_countermeasures 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_drop_unencrypted 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Setting scan request: 0 sec 100000 usec 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Added interface wlan0 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Wireless event: cmd=0x8b06 len=8 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RX ctrl_iface - hexdump_ascii(len=9): 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273):      41 50 5f 53 43 41 4e 20 32                        AP_SCAN 2        
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RX ctrl_iface - hexdump_ascii(len=11): 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273):      41 44 44 5f 4e 45 54 57 4f 52 4b                  ADD_NETWORK      
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE: ADD_NETWORK 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RX ctrl_iface - hexdump_ascii(len=41): [REMOVED] 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE: SET_NETWORK id=0 name='ssid' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE: value - hexdump_ascii(len=22): [REMOVED] 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): ssid - hexdump_ascii(len=11): 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273):      63 6f 6d 6d 75 6e 69 6d 65 73 68                  communimesh      
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): _iface - hexdump_ascii(len=20): [REMOVED] 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE: SET_NETWORK id=0 name='mode' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE: value - hexdump_ascii(len=1): [REMOVED] 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): mode=1 (0x1) 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RX ctrl_iface - hexdump_ascii(len=27): [REMOVED] 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE: SET_NETWORK id=0 name='key_mgmt' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE: value - hexdump_ascii(len=4): [REMOVED] 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): key_mgmt: 0x4 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RX ctrl_iface - hexdump_ascii(len=16): 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273):      45 4e 41 42 4c 45 5f 4e 45 54 57 4f 52 4b 20 30   ENABLE_NETWORK 0 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE: ENABLE_NETWORK id=0 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Setting scan request: 0 sec 0 usec 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): State: DISCONNECTED -> SCANNING 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Trying to associate with SSID 'communimesh' 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Cancelling scan request 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WPA: clearing own WPA/RSN IE 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Automatic auth_alg selection: 0x1 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WPA: clearing AP WPA IE 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WPA: clearing AP RSN IE 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WPA: clearing own WPA/RSN IE 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): No keys have been configured - skip key clearing 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_drop_unencrypted 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): State: SCANNING -> ASSOCIATING 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WEXT: Operstate: linkmode=-1, operstate=5 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_associate 
Sep  4 18:32:01 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Association request to the driver failed 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): ication timeout: 5 sec 0 usec 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAPOL: External notification - portControl=ForceAuthorized 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE monitor attached - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 36 34 2d 32 00 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Wireless event: cmd=0x8b1a len=19 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Authentication with 00:00:00:00:00:00 timed out. 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 36 34 2d 32 00 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Added BSSID 00:00:00:00:00:00 into blacklist 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): State: ASSOCIATING -> DISCONNECTED 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WEXT: Operstate: linkmode=-1, operstate=5 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): No keys have been configured - skip key clearing 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAPOL: External notification - portEnabled=0 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAPOL: External notification - portValid=0 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Setting scan request: 0 sec 0 usec 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): State: DISCONNECTED -> SCANNING 
Sep  4 18:32:06 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Trying to associate with SSID 'communimesh' 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): 1 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 36 34 2d 32 00 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Cancelling scan request 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WPA: clearing own WPA/RSN IE 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Automatic auth_alg selection: 0x1 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WPA: clearing AP WPA IE 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WPA: clearing AP RSN IE 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WPA: clearing own WPA/RSN IE 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): No keys have been configured - skip key clearing 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_drop_unencrypted 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): State: SCANNING -> ASSOCIATING 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): WEXT: Operstate: linkmode=-1, operstate=5 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): wpa_driver_wext_associate 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Association request to the driver failed 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 34 35 36 34 2d 32 00 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Setting authentication timeout: 5 sec 0 usec 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): EAPOL: External notification - portControl=ForceAuthorized 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Wireless event: cmd=0x8b1a len=19 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP]) 
Sep  4 18:32:08 mark-laptop NetworkManager: <information>^Iwpa_supplicant(5273): Wireless event: cmd=0x8b19 len=8 
Sep  4 18:32:10 mark-laptop NetworkManager: <debug info>^I[1188923530.017754] nm_device_802_11_wireless_get_activation_ap (): Forcing AP 'communimesh' 
Sep  4 18:32:10 mark-laptop NetworkManager: <information>^IUser Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / communimesh 
Sep  4 18:32:10 mark-laptop NetworkManager: <information>^IDeactivating device wlan0. 
Sep  4 18:32:10 mark-laptop NetworkManager: <information>^IActivation (wlan0): cancelling... 
Sep  4 18:32:10 mark-laptop NetworkManager: <information>^IActivation (wlan0) cancellation handler scheduled... 
Sep  4 18:32:10 mark-laptop NetworkManager: <information>^IActivation (wlan0): waiting for device to cancel activation. 
Sep  4 18:32:10 mark-laptop NetworkManager: <information>^IActivation (wlan0) cancellation handled. 

```

Here is my /etc/network/interfaces file:-
```
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.10.166
netmask 255.255.0.0
wireless-essid communimesh

auto wlan0

iface eth0 inet dhcp
address 192.168.10.234
netmask 255.255.255.0
gateway 192.168.10.58

auto eth0

```

I suspect that the problem is that my BSSID is not set, but despite diligent googling I am unable to discover how this is done.

Any ideas?

Thanks & regards.

---

