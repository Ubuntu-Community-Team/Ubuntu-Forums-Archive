---
title: "wpa_supplicant errors connecting to WPA PEAP MSCHAPV2 (Radius) WIFI network"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by blak on 2008-10-06
I have Ubuntu - Hardy Heron 8.04 on an eeepc 1000h.

I am using wpa_supplicant (as wicd,network manager, etc. have not worked) to connect to my universities wireless network "uwf-argo-air" and I am getting errors.

Here is everything I have logged, hopefully someone can tell me what I have wrong if anything?

Supposedly it has been possible for someone to connect to the network with wpa_supplicant, so that is why I am using it.


This is my wpa_supplicant.conf file:

```
ctrl_interface=/var/run/wpa_supplicant

# .conf for University wifi
network={
        ssid="uwf-argo-air"
        scan_ssid=1
        key_mgmt=IEEE8021X
        eap=PEAP
        identity="myusername"
        password="mypassword"
        phase2="auth=MSCHAPV2"
}

```



This is what happens when I try to run wpa_supplicant with the .conf file I have... we get an association but then shortly after it disconnects...


```
user@mycomp:/etc/wpa_supplicant$ sudo wpa_supplicant -dd -Dwext -ira0 -c/etc/wpa_supplicant/wpa_supplicant.conf
Initializing interface 'ra0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=12):
     75 77 66 2d 61 72 67 6f 2d 61 69 72               uwf-argo-air    
scan_ssid=1 (0x1)
key_mgmt: 0x8
eap methods - hexdump(len=16): 00 00 00 00 19 00 00 00 00 00 00 00 00 00 00 00
identity - hexdump_ascii(len=4):
     61 45 6d 18                                       myusername            
password - hexdump_ascii(len=5): [REMOVED]
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3d 4d 53 43 48 41 50 56 32            auth=MSCHAPV2   
Priority group 0
   id=0 ssid='uwf-argo-air'
Initializing interface (2) 'ra0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWMODE]: Network is down
Could not configure driver to use managed mode
SIOCGIWRANGE: WE(compiled)=22 WE(source)=14 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:13:da:aa:6a:54
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface ra0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ra0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=12):
     75 77 66 2d 61 72 67 6f 2d 61 69 72               uwf-argo-air    
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
CTRL_IFACE monitor attached - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 37 39 35 00
RX ctrl_iface - hexdump_ascii(len=10):
     49 4e 54 45 52 46 41 43 45 53                     INTERFACES      
RX ctrl_iface - hexdump_ascii(len=6):
     53 54 41 54 55 53                                 STATUS          
ioctl[SIOCGIFADDR]: Cannot assign requested address
RX ctrl_iface - hexdump_ascii(len=13):
     4c 49 53 54 5f 4e 45 54 57 4f 52 4b 53            LIST_NETWORKS   
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
Scan timeout - try to get results
Received 1703 bytes of scan results (21 BSSes)
Scan results: 21
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:13:c4:78:60:b0 ssid='uwf-argo-air' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:17:0f:36:10:50 ssid='uwf-argo-air' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0b:85:88:70:6e ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:0b:85:88:9b:5f ssid='uwf-argo-air' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:0b:85:88:9b:7c ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:0b:85:88:9b:7b ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:0b:85:88:70:6b ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
7: 00:0b:85:88:70:6a ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
8: 00:0b:85:88:9b:5d ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
9: 00:0b:85:88:9b:7e ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
10: 00:0b:85:88:9b:7d ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
11: 00:0b:85:88:70:6f ssid='uwf-argo-air' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
12: 00:0b:85:88:70:6c ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
13: 00:0b:85:88:6d:3f ssid='uwf-argo-air' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
14: 00:0b:85:88:70:6d ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
15: 00:11:21:89:d8:f0 ssid='uwf-argo-air' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
16: 00:11:21:89:e4:10 ssid='uwf-argo-air' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
17: 00:0b:85:88:98:cf ssid='uwf-argo-air' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
18: 00:21:29:84:3e:31 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
19: 02:9d:0a:e8:57:40 ssid='hpsetup' wpa_ie_len=0 rsn_ie_len=0 caps=0x2
   skip - no WPA/RSN IE
20: 00:17:3f:7c:ee:7c ssid='belkin54g' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:13:c4:78:60:b0 ssid='uwf-argo-air' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:13:c4:78:60:b0 ssid='uwf-argo-air'
Trying to associate with 00:13:c4:78:60:b0 (SSID='uwf-argo-air' freq=2412 MHz)
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 37 39 35 00
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=20
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=6):
     53 54 41 54 55 53                                 STATUS          
ioctl[SIOCGIFADDR]: Cannot assign requested address
RX ctrl_iface - hexdump_ascii(len=13):
     4c 49 53 54 5f 4e 45 54 57 4f 52 4b 53            LIST_NETWORKS   
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=8
AssocReq IE wireless event - hexdump(len=0):
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:13:c4:78:60:b0
Association info event
req_ies - hexdump(len=0):
WPA: clearing own WPA/RSN IE
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:13:c4:78:60:b0
No keys have been configured - skip key clearing
Associated with 00:13:c4:78:60:b0
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 37 39 35 00
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=6):
     53 54 41 54 55 53                                 STATUS          
ioctl[SIOCGIFADDR]: Cannot assign requested address
RX ctrl_iface - hexdump_ascii(len=13):
     4c 49 53 54 5f 4e 45 54 57 4f 52 4b 53            LIST_NETWORKS   

```



This is the code right before and after we have failure or disconnect....



```
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
CTRL_IFACE monitor detached - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 35 37 00
CTRL_IFACE monitor attached - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 35 39 00
CTRL_IFACE monitor attached - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 36 31 00
RX ctrl_iface - hexdump_ascii(len=10):
     49 4e 54 45 52 46 41 43 45 53                     INTERFACES      
RX ctrl_iface - hexdump_ascii(len=6):
     53 54 41 54 55 53                                 STATUS          
ioctl[SIOCGIFADDR]: Cannot assign requested address
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
TX EAPOL - hexdump(len=4): 01 01 00 00
Authentication with 00:13:c4:78:60:b0 timed out.
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 36 31 00
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 35 39 00
sendmsg(CTRL_IFACE monitor): No such file or directory
Added BSSID 00:13:c4:78:60:b0 into blacklist
wpa_driver_wext_disassociate
No keys have been configured - skip key clearing
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=12):
     75 77 66 2d 61 72 67 6f 2d 61 69 72               uwf-argo-air    
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 36 31 00
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 35 39 00
sendmsg(CTRL_IFACE monitor): No such file or directory
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: SCANNING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 36 31 00
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 35 39 00
sendmsg(CTRL_IFACE monitor): No such file or directory
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 3
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 36 31 00
CTRL_IFACE monitor send - hexdump(len=23): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 32 30 36 2d 38 35 39 00
sendmsg(CTRL_IFACE monitor): No such file or directory
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=6):
     53 54 41 54 55 53                                 STATUS          
ioctl[SIOCGIFADDR]: Cannot assign requested address
RX ctrl_iface - hexdump_ascii(len=13):
     4c 49 53 54 5f 4e 45 54 57 4f 52 4b 53            LIST_NETWORKS   

```



I have wpa_supplicant working on every other network type, wep 128 Hex, wpa etc. just not on this university wifi with this radius server they use.

If anyone can figure out what on earth is going on here I would be greatly appreciative!

Thanks,
blak

---

