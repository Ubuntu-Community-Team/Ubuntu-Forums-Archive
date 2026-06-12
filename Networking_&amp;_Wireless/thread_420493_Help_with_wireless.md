---
title: "Help with wireless"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by hulluPeruna on 2007-04-23
Hi I am trying hard to get my fritz usb wireless module working under feisty again like it did under edgy. 

I am tried the native fritz drivers and the ndiswrapper solution. But had no luck with both. I am able to do scans with the hardware but not able to connect. here are my settings:
/etc/wpa_supplicant/wpa_supplicant.conf:
[INDENT]
 ctrl_interface=/var/run/wpa_supplicant
 ap_scan=1

 network={
 ssid="XXXXX"
 scan_ssid=1
 proto=WPA
 key_mgmt=WPA-PSK
 pairwise=TKIP
 #psk="XXXXXXXXXXXXX"
 psk=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
 }[/INDENT]

and if I do a 
# sudo ifconfig wlan0 up && wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -dd
I get a "[COLOR="Red"]No keys have been configured - skip key clearing[/COLOR]" is that my problem and if yes how do I fix it????


[INDENT]
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=1
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=8):
     48 6f 6d 65 4e 65 74 32                           XXXXXXXX
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK - hexdump(len=32): [REMOVED]
Line 12: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='XXXXXXXXX'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=9 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:04:0e:cd:7d:ba
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=8):
     48 6f 6d 65 4e 65 74 32                           XXXXXXXXX
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 70 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:04:0e:d5:20:98 ssid='XXXXXXXXXX' wpa_ie_len=26 rsn_ie_len=0 caps=0x0
   selected based on WPA IE
Trying to associate with 00:04:0e:d5:20:98 (SSID='XXXXXXXX' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=16
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Cancelling scan request
[/INDENT]

---

### Post by zorkerz on 2007-04-23
So your trying to use an external usb wireless key? There are no linux drivers on the makers site or they don't work? And you are using feisty now? I am just trying to make sure i understand. Have you found any of the ndiswrapper how tos im not sure they will work for your device but could be helpful.
good luck

---

