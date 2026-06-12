---
title: "cant connect manually to wireless network"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by sherin on 2008-07-30
its been a hard time for me connecting to my wireless network .  nm-applet way sucks... :( 
So i decided to do it manually . My hardware is  [B]Intel(R) PRO/Wireless 3945ABG .
[/B]But while following a howto in the ubuntu wiki pages (using wpa_supplicant) , i cant successfully connect to wireless even if the scan results have the network detected. 

here is the log for wpa_supplicant ...

```
root@po:~# wpa_supplicant -Dwext -iwlan0 -c/root/wpa_supplicant.conf -w -dd
Initializing interface 'wlan0' conf '/root/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/root/wpa_supplicant.conf' -> '/root/wpa_supplicant.conf'
Reading configuration file '/root/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=4):
     68 6f 6d 65                                       home            
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='home'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:13:02:c4:e2:1c
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 236 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:7e:eb:b8:4b ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1d:7e:eb:b8:4b ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 236 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:7e:eb:b8:4b ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1d:7e:eb:b8:4b ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 236 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:7e:eb:b8:4b ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:1d:7e:eb:b8:4b ssid='' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No suitable AP found.


```i dont have any issues with the router. when tested on a windows box, i was able to connect to the same network . only ubuntu is giving me problems. 
what might be going wrong for me ? :confused:

---

### Post by df6269 on 2008-07-30
Can you output detail information about wpa_supplicant.conf file?

---

### Post by sherin on 2008-08-03
network={
    ssid="home"
    #psk="getintohome"
    psk=f963b8be32f11b7279cf78effa0791d3fd4d1943d1ec5e77a5695ab5cfcea768
}

---

### Post by kevdog on 2008-08-03
You need more info in the supplicant file than that.  See the stick thread at the top of the networking forums.

Thanks.

---

### Post by sherin on 2008-08-21
i guess network manager path became hard for me because of some issues with iwl3945 driver . i installed linux-backports-modules-hardy-generic from backports repository and it worked for me using nm-applet. :guitar: 

probably i can try the manual way later and post the results here ... thanks kevdog, for your support.

---

