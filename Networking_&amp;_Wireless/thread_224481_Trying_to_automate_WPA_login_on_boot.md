---
title: "Trying to automate WPA login on boot"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by Ragueneau on 2006-07-28
...but first, I need to get the wireless working at all.  

I'm using a Netgear WG511v2 with the Intersil ISL3890 chipset on Xubuntu Dapper 6.06.  I'm using the SMC 2802w driver in ndiswrapper, which works when I don't use encryption.  

To set up WPA, I've been using the tutorial here:
[http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa](http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa)

however I haven't gotten very far.  ```
sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && dhclient wlan0
``` fails to grab an IP from my router, so I ran ```
sudo dhclient -r wlan0 && ifconfig wlan0 down && killall wpa_supplicant
sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
``` which outputs ```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=2
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=8):
     45 74 68 65 72 65 61 6c
PSK - hexdump(len=32): [REMOVED]
key_mgmt: 0x2
proto: 0x1
Priority group 0
   id=0 ssid='MySSID'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECIEVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xd
  capabilities: key_mgmt 0x5 enc 0xf
Own MAC address: 00:09:5b:c8:8f:91
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
Setting scan request: 0 sec 100000 usec
Added interface wlan0
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'MySSID'
Cancelling scan request
WPA: clearing own WPA/RSN IE
WPA: set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 20
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING

```

And it loops between instances of State: DISCONNECTED -> SCANNING until I end it.

Where should I start looking for my problem?

---

