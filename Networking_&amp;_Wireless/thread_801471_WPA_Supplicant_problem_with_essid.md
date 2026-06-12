---
title: "WPA_Supplicant problem with essid"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by Cresta on 2008-05-20
Hello. Can anyone help. I'm still a newby.

I've got an Edimax EW-7128g (RT61) using Ndiswrapper and WPA_Supplicant for the WPA. But it cant see my AP after running

The Ndiswrapper instruction say to  

"...add the following line to .config file:
CONFIG_DRIVER_WEXT=y
CONFIG_CTRL_IFACE=y
Now compile it with “make”..." 

How do I compile it with "make"? 

I've created the /etc/wpa_supplicant.conf correctly..i think and this is what is returned when I run

ifconfig wlan0 up
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

homepc@homepc-desktop:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=7):
     4e 45 54 47 45 41 52                              NETGEAR         
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=22): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='NETGEAR'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0e:2e:4e:7e:67
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 257 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:09:5b:d7:62:bc ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:09:5b:d7:62:bc ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 257 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:09:5b:d7:62:bc ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:09:5b:d7:62:bc ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 257 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:09:5b:d7:62:bc ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:09:5b:d7:62:bc ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 257 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:09:5b:d7:62:bc ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:09:5b:d7:62:bc ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout


Does this make any sence to anyone.
Some guidance would be great
Thankyou All

---

