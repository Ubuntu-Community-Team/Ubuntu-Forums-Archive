---
title: "dell wireless with wpa_supplicant issue"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by ample on 2008-08-03
im trying to connect a laptop with a dell wireless 1350 wlan min-pci card to a linksys wrt54g wireless router.  the router is setup for wpa-psk & tkip, and my wpa_supplicant.conf is written accordingly.  ive installed ndisgtk and loaded the .inf, extracted from the dell driver exe.  ndiswrapper -l yields:
```
user@user-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
```
however, wpa_supplicant yields:
```
user@user-laptop:~$ sudo wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -Dwext -dd
[sudo] password for user: 
Sorry, try again.
[sudo] password for user: 
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=16):
     48 69 6c 6c 73 69 64 65 5f 42 72 65 77 65 72 73   wrt54g
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='wrt54g'
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
Own MAC address: 00:90:96:b8:15:94
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
Received 2310 bytes of scan results (12 BSSes)
Scan results: 12
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:7e:1c:c3:7c ssid='wrt54g' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1d:7e:1c:c3:7c ssid='wrt54g'
Try to find non-WPA AP
Trying to associate with 00:1d:7e:1c:c3:7c (SSID='wrt54g' freq=2437 MHz)
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=24
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=205
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE7273010802040b160c12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIEdd090010180201f4000000)'
Association info event
req_ies - hexdump(len=58): 00 10 48 69 6c 6c 73 69 64 65 5f 42 72 65 77 65 72 73 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=27): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 09 00 10 18 02 01 f4 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1d:7e:1c:c3:7c
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1d:7e:1c:c3:7c
No keys have been configured - skip key clearing
Associated with 00:1d:7e:1c:c3:7c
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:1d:7e:1c:c3:7c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce b4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce b4
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce b4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1d:7e:1c:c3:7c (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 9e 7b e1 b9 3d a8 1f 7d 31 ff fe 57 fe 3b 20 9e e4 e1 b2 98 f4 f6 bf 02 7d 41 54 f3 65 93 07 f8
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 00 9e 7b e1 b9 3d a8 1f 7d 31 ff fe 57 fe 3b 20 9e e4 e1 b2 98 f4 f6 bf 02 7d 41 54 f3 65 93 07 f8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6b 3d 77 92 5e 77 2e 1d c6 56 82 68 86 7a 3b 6a 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1d:7e:1c:c3:7c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce b4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce b4
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce b4 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1d:7e:1c:c3:7c (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 9e 7b e1 b9 3d a8 1f 7d 31 ff fe 57 fe 3b 20 9e e4 e1 b2 98 f4 f6 bf 02 7d 41 54 f3 65 93 07 f8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 da e8 3c dd d2 37 da e9 96 0c 79 df 5a 3c e9 56 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: 4WAY_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_deauthenticate
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
```
any help or suggestions would be appreciated.

-ample

---

### Post by ample on 2008-08-03
the above problem may have been because my passphrase was unencrypted.  it is now encrypted using 'wpa_passphrase ssid passphrase' and this is the new error:
```
user@user-laptop:~$ sudo wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -Dwext -dd
[sudo] password for user: 
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=16):
     48 69 6c 6c 73 69 64 65 5f 42 72 65 77 65 72 73   wrt54g
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
pairwise: 0x8
group: 0x8
Priority group 0
   id=0 ssid='wrt54g'
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
Own MAC address: 00:90:96:b8:15:94
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
Received 2485 bytes of scan results (14 BSSes)
Scan results: 14
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:7e:1c:c3:7c ssid='wrt54g' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1d:7e:1c:c3:7c ssid='wrt54g'
Try to find non-WPA AP
Trying to associate with 00:1d:7e:1c:c3:7c (SSID='wrt54g' freq=2437 MHz)
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=24
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=205
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE7273010802040b160c12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIEdd090010180201f4000000)'
Association info event
req_ies - hexdump(len=58): 00 10 48 69 6c 6c 73 69 64 65 5f 42 72 65 77 65 72 73 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=27): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 09 00 10 18 02 01 f4 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1d:7e:1c:c3:7c
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1d:7e:1c:c3:7c
No keys have been configured - skip key clearing
Associated with 00:1d:7e:1c:c3:7c
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:1d:7e:1c:c3:7c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_nonce - hexdump(len=32): 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 00 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1d:7e:1c:c3:7c (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 7d fe 5b e1 50 2e 73 b5 d0 51 5b bb d8 a9 b8 98 bb 23 9c 9b a0 8e 6d c0 b6 03 f7 08 8b ed 45 6b
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 00 7d fe 5b e1 50 2e 73 b5 d0 51 5b bb d8 a9 b8 98 bb 23 9c 9b a0 8e 6d c0 b6 03 f7 08 8b ed 45 6b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 86 5f 05 e5 83 5c e7 8e f9 7c 7d f2 12 18 85 71 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1d:7e:1c:c3:7c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1d:7e:1c:c3:7c (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 7d fe 5b e1 50 2e 73 b5 d0 51 5b bb d8 a9 b8 98 bb 23 9c 9b a0 8e 6d c0 b6 03 f7 08 8b ed 45 6b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 fe 7c 3e 3d 10 0d 7d 38 c9 c7 ec 7c ba 2b f6 c4 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1d:7e:1c:c3:7c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 02 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 02 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1d:7e:1c:c3:7c (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 02 7d fe 5b e1 50 2e 73 b5 d0 51 5b bb d8 a9 b8 98 bb 23 9c 9b a0 8e 6d c0 b6 03 f7 08 8b ed 45 6b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 82 24 3a 43 22 ef e6 99 54 c1 b4 b0 12 e4 32 ea 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RX EAPOL from 00:1d:7e:1c:c3:7c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 03 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 03 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce ba 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1d:7e:1c:c3:7c (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 03 7d fe 5b e1 50 2e 73 b5 d0 51 5b bb d8 a9 b8 98 bb 23 9c 9b a0 8e 6d c0 b6 03 f7 08 8b ed 45 6b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7e 7c 8b 57 9e c3 cd 78 ab fe 70 6c aa d6 9d fc 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Setting scan request: 0 sec 100000 usec
Added BSSID 00:1d:7e:1c:c3:7c into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: 4WAY_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=205
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE7273010802040b160c12182432043048606cdd160050f20101000050f20201000050f20201000050f202 RespIEdd090010180201f4000000)'
Association info event
req_ies - hexdump(len=58): 00 10 48 69 6c 6c 73 69 64 65 5f 42 72 65 77 65 72 73 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=27): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 09 00 10 18 02 01 f4 00 00 00
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1d:7e:1c:c3:7c
State: SCANNING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1d:7e:1c:c3:7c
No keys have been configured - skip key clearing
Associated with 00:1d:7e:1c:c3:7c
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b19 len=8
Received 3205 bytes of scan results (17 BSSes)
Scan results: 17
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:7e:1c:c3:7c ssid='wrt54g' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1d:7e:1c:c3:7c ssid='wrt54g'
Try to find non-WPA AP
Already associated with the selected AP.
RX EAPOL from 00:1d:7e:1c:c3:7c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce bb 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce bb
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce bb 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1d:7e:1c:c3:7c (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 34 65 8d 32 2e db 32 e4 2c 7a 40 4d da be 01 dd 73 b4 27 84 bd e9 e2 62 06 51 17 70 3e 64 5a 07
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 34 65 8d 32 2e db 32 e4 2c 7a 40 4d da be 01 dd 73 b4 27 84 bd e9 e2 62 06 51 17 70 3e 64 5a 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 24 0f 73 63 03 12 77 fc 2a 3e c0 c5 62 54 93 ac 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1d:7e:1c:c3:7c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 02 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce bb 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce bb
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 02 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce bb 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1d:7e:1c:c3:7c (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 02 34 65 8d 32 2e db 32 e4 2c 7a 40 4d da be 01 dd 73 b4 27 84 bd e9 e2 62 06 51 17 70 3e 64 5a 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 86 aa c3 c8 16 37 4b 62 7a 68 d5 b8 5f 0a c0 99 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RX EAPOL from 00:1d:7e:1c:c3:7c
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 03 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce bb 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce bb
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 03 47 b4 e1 1c 34 f6 41 a1 9a 2f c3 9c 12 ae f9 69 0a af 22 2f 5e 10 a0 48 ec 3e c7 52 6d cf ce bb 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1d:7e:1c:c3:7c (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 03 34 65 8d 32 2e db 32 e4 2c 7a 40 4d da be 01 dd 73 b4 27 84 bd e9 e2 62 06 51 17 70 3e 64 5a 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 92 68 a5 25 e1 1f 3d d5 8e 2e 65 5b 59 73 c1 d0 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: 4WAY_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_deauthenticate
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Removed BSSID 00:1d:7e:1c:c3:7c from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
```

---

### Post by jobano on 2008-08-04
hi,
it will appear stupid but try your wpa_supplicant command at boot, just after having killed other eventual network process (dhclient, NetworkManager...)
and do it from text-console (Alt-F1), even before having graphicaly logged on

I have on my laptop a strange comportement: wpa_supplicant connects itself only from text-console, not graphical one...

---

### Post by jimv on 2008-08-04
I'd try installing WICD instead of Network Manager.  It will handle all the WPA Supplicant configuration for you.

---

### Post by jobano on 2008-08-04
wicd tried, nice app, i just discover it, but still not able to finish authentication...

i still connect through console / wpa_supplicant

into a graphical terminal window ( Terminal 0.2.8 ), i get this:
```
root:~# wpa_supplicant -c/etc/wpa_supplicant.conf -w -Dwext -iwlan0
Trying to associate with 4e:a2:3e:57:2f:c8 (SSID='lesPDsDu4e' freq=2412 MHz)
Associated with 4e:a2:3e:57:2f:c8
Associated with 4e:a2:3e:57:2f:c8
Associated with 4e:a2:3e:57:2f:c8
Associated with 4e:a2:3e:57:2f:c8 ...ever and ever...
```

just after that, i switch to a basic text console (tty), and launch the same command:
```
root@ldellou:~# wpa_supplicant -c/etc/wpa_supplicant.conf -w -Dwext -iwlan0
Trying to associate with 4e:a2:3e:57:2f:c8 (SSID='lesPDsDu4e' freq=2412 MHz)
Associated with 4e:a2:3e:57:2f:c8
WPA: Key negotiation completed with 4e:a2:3e:57:2f:c8 [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 4e:a2:3e:57:2f:c8 completed (auth) [id=0 id_str=]
```

then dhclient wlan0 and i'm online, but it's not really useful...

---

### Post by ample on 2008-08-04
already tried wicd and ended up switching back to n-m.  just tried running wpa_supplicant in tty1 with the same errors.

heres a qwick look at dmesg if it helps:
```
[  913.562069] wlan0: authenticated
[  913.562073] wlan0: associate with AP 00:1d:7e:1c:c3:7c
[  913.565168] wlan0: RX ReassocResp from 00:1d:7e:1c:c3:7c (capab=0x11 status=0 aid=2)
[  913.565174] wlan0: associated
[  914.107086] wlan0: no IPv6 routers present
[  917.559685] wlan0: RX deauthentication from 00:1d:7e:1c:c3:7c (reason=15)
[  917.559690] wlan0: deauthenticated
[  918.555301] wlan0: authenticate with AP 00:1d:7e:1c:c3:7c
[  918.556797] wlan0: RX authentication from 00:1d:7e:1c:c3:7c (alg=0 transaction=2 status=0)
[  918.556801] wlan0: authenticated
[  918.556805] wlan0: associate with AP 00:1d:7e:1c:c3:7c
[  918.559574] wlan0: RX ReassocResp from 00:1d:7e:1c:c3:7c (capab=0x11 status=0 aid=2)
[  918.559578] wlan0: associated
[  922.554249] wlan0: RX deauthentication from 00:1d:7e:1c:c3:7c (reason=15)
[  922.554255] wlan0: deauthenticated
[  923.550081] wlan0: authenticate with AP 00:1d:7e:1c:c3:7c
[  923.567574] wlan0: RX authentication from 00:1d:7e:1c:c3:7c (alg=0 transaction=2 status=0)
[  923.567582] wlan0: authenticated
[  923.567587] wlan0: associate with AP 00:1d:7e:1c:c3:7c
[  923.555623] wlan0: RX ReassocResp from 00:1d:7e:1c:c3:7c (capab=0x11 status=0 aid=2)
[  923.555629] wlan0: associated
[  927.550015] wlan0: RX deauthentication from 00:1d:7e:1c:c3:7c (reason=15)
[  927.550021] wlan0: deauthenticated
```
apparently im getting RX deauthenticated(reason=15), but ive tried looking up the reason with no luck so far.

---

### Post by jobano on 2008-08-05
arf,

i will watch my dmesg tonight, it definitely looks like my problem...

just in case, in my wpa_supplicant.conf, the pwd is in clear text.
I come back with more from my conf tonight

---

