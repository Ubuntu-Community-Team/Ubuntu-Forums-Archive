---
title: "wpa_supplicant can't start: ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by vlad.genie on 2007-02-26
OS: Ubuntu 6.10
Card: Intel PRO/Wireless 3945ABG

I have all wifi-card drivers installed. I have found active AP with WPA-PSK turned off, recieved IP-adress with DHCP and successfully made ping to local server.

Now I have to establish network connection with WPA-PSK on. This is not happens :(

Here is log:

```
vlad@vlad-ubuntu:~$ sudo wpa_supplicant -c/etc/wpa_supplicant.conf -ieth1 -d
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='ZG560'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=20 WE(source)=16 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:13:02:3c:de:1a
wpa_driver_hostap_set_wpa: enabled=1
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_countermeasures: enabled=0
wpa_driver_hostap_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 260 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:a0:c5:94:31:87 ssid='ZG560' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:a0:c5:94:31:87 (SSID='ZG560' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_hostap_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_hostap_associate
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=14
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:a0:c5:94:31:87 into blacklist
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
Wireless event: cmd=0x8b1a len=14
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
State: DISCONNECTED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
Wireless event: cmd=0x8b1a len=8
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
State: DISCONNECTED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 3
State: DISCONNECTED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 4
State: SCANNING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
Scan timeout - try to get results
Received 261 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:a0:c5:94:31:87 ssid='ZG560' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:a0:c5:94:31:87 (SSID='ZG560' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_hostap_set_drop_unencrypted: enabled=1
State: DISCONNECTED -> ASSOCIATING
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_hostap_associate
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=14
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:a0:c5:94:31:87 blacklist count incremented to 2
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 5
State: DISCONNECTED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
q
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 6
State: DISCONNECTED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
wpa_driver_hostap_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported Failed to set encryption.
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: DISCONNECTED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_hostap_set_wpa: enabled=0
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
wpa_driver_hostap_set_drop_unencrypted: enabled=0
wpa_driver_hostap_set_countermeasures: enabled=0
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Removed BSSID 00:a0:c5:94:31:87 from blacklist (clear)
Cancelling scan request

```

What can it be? How can I establish connection?

Thanks for your help in advance.

---

