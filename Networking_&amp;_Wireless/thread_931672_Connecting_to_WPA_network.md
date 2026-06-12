---
title: "Connecting to WPA network"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by antisho on 2008-09-27
I'm trying to connect to a WPA network, which I know to be WPA2-Enterprise with PEAP and MSCHAPv2. I have a Cisco wireless card, which connects fine to unsecured networks, but I don't know what driver it uses.

I have the following in my wpa_supplicant.conf:

```
ctrl_interface=/var/run/wpa_supplicant
network={
	ssid=""
	key_mgmt=WPA-EAP
	proto=WPA2
	eap=PEAP
	phase2="auth=MSCHAPV2"
	identity="<foo>"
}
```

However, when I run sudo wpa_supplicant -i<bar> -c/etc/wpa_supplicant.conf, I get

```
ioctl[SIOCGIFADDR]: Cannot assign requested address
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCGIFADDR]: Cannot assign requested address
```

If I add -d, I get

```
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
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
Received 217 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1a:a2:fc:4c:20 ssid='' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - disabled
   selected based on RSN IE
   selected WPA AP 00:1a:a2:fc:4c:20 ssid=''
Try to find non-WPA AP
Trying to associate with 00:1a:a2:fc:4c:20 (SSID='' freq=2412 MHz)
CTRL_IFACE monitor send - hexdump(len=22): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 39 34 31 34 2d 31 00
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 16 key_mgmt 1 proto 2
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 00 00
WPA: set AP RSN IE - hexdump(len=24): 30 16 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 01 00 00 00 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 01 00 00
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
ioctl[SIOCSIWGENIE]: Operation not supported
Association request to the driver failed
CTRL_IFACE monitor send - hexdump(len=22): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 39 34 31 34 2d 31 00
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 217 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1a:a2:fc:4c:20 ssid='' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   skip - disabled
   selected based on RSN IE
   selected WPA AP 00:1a:a2:fc:4c:20 ssid=''
Try to find non-WPA AP
Already associated with the selected AP.
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b1a len=8
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=6):
     53 54 41 54 55 53                                 STATUS          
ioctl[SIOCGIFADDR]: Cannot assign requested address
RX ctrl_iface - hexdump_ascii(len=13):
     4c 49 53 54 5f 4e 45 54 57 4f 52 4b 53            LIST_NETWORKS   
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=10):
     44 49 53 43 4f 4e 4e 45 43 54                     DISCONNECT      
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
CTRL-EVENT-TERMINATING - signal 2 received
CTRL_IFACE monitor send - hexdump(len=22): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 32 39 34 31 34 2d 31 00
Removing interface eth2
```

Originally I specified a ssid in wpa_supplicant.conf, but wpa_supplicant kept scanning and coming up with only networks named '', so I removed it. But it seems that it still can't connect for some reason. Does anyone know what I can do to fix this?

---

