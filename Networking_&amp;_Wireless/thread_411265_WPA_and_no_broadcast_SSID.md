---
title: "WPA and no broadcast SSID"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by n8wood on 2007-04-16
I know there is no security advantage to hiding the SSID, but the network I need to connect to has a hidden SSID. This is beyond my control unfortunately.

So I'm using an Atheros based card, and from my test at home I was able to successfully connect to a WPA network that is broadcasting it's SSID. When I try at work I cannot connect, but I am successful in Windows. I have tried using Network Manager and eventually moved on to wpa_supplicant directly through the CLI. Here is what my wpa_supplicant.conf file looks like:

```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2
network={
       ssid="secure"
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk=my code

```

Here is the output of wpa_supplicant:
```

Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A' bridge
 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     73 65 63 75 72 65                                 secure          
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): 2b 85 c9 63 fd 47 36 f3 49 c9 f8 6b 77 0f 4a 80 e0 90 93 77 e3 34 83 23 75 15 64 9e
 4d 86 c0 cc
Priority group 0
   id=0 ssid='secure'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=13 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:40:f4:de:8d:be
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface ath0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'secure'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00
 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_madwifi_associate
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=14
Ignore event for foreign ifindex 2
CTRL_IFACE monitor attached - hexdump(len=21): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 36 38 38 38 2d 30
 00
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=6):
     53 54 41 54 55 53                                 STATUS          

```

I would greatly appreciate any help troubleshooting this. Thank you.

---

### Post by n8wood on 2007-04-17
any ideas?

---

### Post by spd106 on 2007-04-17
Try adding the line "scan_ssid=1" to the network section of your wpa_supplicant.conf and if you're on 6.10 (Edgy) switch to the wext driver rather than madwifi, which is better on 6.06 LTS (Dapper).

---

### Post by n8wood on 2007-04-17
I was able to finally get it working! This is what my wpa_supplicant.conf looks like:

```
ap_scan=1

network={
       ssid="secure"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk=something
}

```

---

