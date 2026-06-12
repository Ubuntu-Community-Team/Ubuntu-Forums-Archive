---
title: "Didn't understand what to do for a WG511v2 card"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by LeJediGris on 2007-06-14
Hi all, 

Since a couple of weeks i try to configure my netgear WG511v2 (China) with Ubuntu Feisty.

I've read the tutos from the French Ubuntu forums. They indicate to use ndiswrapper. I've already withdraw network-manager and put all the config manually.

I've seen on this forum that you can use madwifi for the WG511v2 (china) atheros chipset.

With ndiswrapper wpa supplicant said :

```
root@thierry-laptop:/etc/default# wpa_supplicant -c/etc/wpa_supplicant.conf -w -d -Dndiswrapper -iwlan0
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group='0' (DEPRECATED)
eapol_version=1
ap_scan=1
fast_reauth=1
Line 21: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='WIFI_TS'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Added alternative ifindex 5 (wifi0) for wireless events
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:18:4d:6d:8f:55
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
ctrl_interface_group=0
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=7):
     57 49 46 49 5f 54 53                              WIFI_TS         
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 2798 bytes of scan results (13 BSSes)
Scan results: 13
Selecting BSS from priority group 0
0: fe:fe:09:eb:9c:c0 ssid='WIFI_TS' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with fe:fe:09:eb:9c:c0 (SSID='WIFI_TS' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXx
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID fe:fe:09:eb:9c:c0 into blacklist
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 2636 bytes of scan results (12 BSSes)
Scan results: 12
Selecting BSS from priority group 0
0: fe:fe:09:eb:9c:c3 ssid='freephonie' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: fe:fe:09:eb:9c:c0 ssid='WIFI_TS' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with fe:fe:09:eb:9c:c0 (SSID='WIFI_TS' freq=2412 MHz)
```

Seems to be a trouble around the ndis driver and wpa interface with WPA...

Everything is OK for the rest of the config (driver ok hard present) iwlist OK with wlan0.....

So are you sure that the madwifi driver works well with the card ?? (strange for me..)

Thanks for the answer,

A bientôt :D

---

### Post by LeJediGris on 2007-06-14
Just one mistake..... my chipset is NOT ATHEROS but really a Marvell 88w8335 (Libertas).... so i've to cope with ndiswrapper....

Any comment/advise looking at my wpa_supplicant output (-d) ??

Thanks from Paris:KS

---

### Post by LeJediGris on 2007-06-14
Thanks to the forum's tuto about WPA  (HOWTO : wpa encryption) my connection works fine now.

Simply don't forget to put "wext" instead of "ndiswrapper" for the wpa parameters !!

Thanks a lot

---

