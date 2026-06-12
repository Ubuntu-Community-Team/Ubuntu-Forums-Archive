---
title: "Wireless WPA problems with a Intel PRO/Wireless 2200BG card"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by RobbingDaHood on 2008-07-14
I have a Dell Inspiron 6000 laptop [http://reviews.cnet.com/laptops/dell-inspiron-6000/4507-3121_7-31257675.html](http://reviews.cnet.com/laptops/dell-inspiron-6000/4507-3121_7-31257675.html)

and I have installed Ubuntu 8.04 on it. 

Then I wanted to connect to my D-Link router wireless WPA encrypted network, but my network manager where stuck in a loop while trying to connect. 

Then I checked if my network card were WPA supported by Ubuntu [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel) and found out it were. 

That page lead me to a how to [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) that were very helpful. I followed every step in that how to, I got some problems and some of them I have solved with some good and fast help on the IRC.

But now my wpa_supplicant freezes when I use it:

```
sudo wpa_supplicant -w -Dwext -i eth1 -c/etc/wpa_supplicant.conf -dd
```  

My wireless is eth1. 

The output in the terminal is:

```

RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
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
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Already associated with a configured network - generating associated event
Association info event
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
^AEAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=8
Received 777 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:11:57:15:11 ssid='DanielErSej' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1b:11:57:15:11 ssid='DanielErSej'
Try to find non-WPA AP
Trying to associate with 00:1b:11:57:15:11 (SSID='DanielErSej' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: ASSOCIATED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 60 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=19
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1b:11:57:15:11
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1b:11:57:15:11
No keys have been configured - skip key clearing
Network configuration found for the current AP
WPA: Using WPA IE from AssocReq to set cipher suites
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Associated with 00:1b:11:57:15:11
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from 00:1b:11:57:15:11
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 f8 f5 31 99 af 2f 1d b5 a9 a8 f9 91 68 41 5d 2a 81 f3 b0 7e 00 8a 94 8a 9e 8a ee 5c cb 7e f5 6a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): f8 f5 31 99 af 2f 1d b5 a9 a8 f9 91 68 41 5d 2a 81 f3 b0 7e 00 8a 94 8a 9e 8a ee 5c cb 7e f5 6a
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 f8 f5 31 99 af 2f 1d b5 a9 a8 f9 91 68 41 5d 2a 81 f3 b0 7e 00 8a 94 8a 9e 8a ee 5c cb 7e f5 6a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1b:11:57:15:11 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): fb ef fc 9e e3 a5 d6 a2 9d 85 ae 01 17 80 26 c2 a2 f4 10 29 f3 01 78 2c 2b 7e 1d 35 8b 58 7c 73
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 fb ef fc 9e e3 a5 d6 a2 9d 85 ae 01 17 80 26 c2 a2 f4 10 29 f3 01 78 2c 2b 7e 1d 35 8b 58 7c 73 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f3 24 2a a5 45 9d f3 d0 85 8c 6a 88 a1 46 05 42 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1b:11:57:15:11
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 f8 f5 31 99 af 2f 1d b5 a9 a8 f9 91 68 41 5d 2a 81 f3 b0 7e 00 8a 94 8a 9e 8a ee 5c cb 7e f5 6a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a3 e3 f1 7f a0 8a ce 87 35 3e 1c 82 0e 7c f3 1c 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): f8 f5 31 99 af 2f 1d b5 a9 a8 f9 91 68 41 5d 2a 81 f3 b0 7e 00 8a 94 8a 9e 8a ee 5c cb 7e f5 6a
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): a3 e3 f1 7f a0 8a ce 87 35 3e 1c 82 0e 7c f3 1c
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 f8 f5 31 99 af 2f 1d b5 a9 a8 f9 91 68 41 5d 2a 81 f3 b0 7e 00 8a 94 8a 9e 8a ee 5c cb 7e f5 6a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a3 e3 f1 7f a0 8a ce 87 35 3e 1c 82 0e 7c f3 1c 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1b:11:57:15:11 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: No WPA/RSN IE for this AP known. Trying to get from scan results
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: Found the current AP from updated scan results
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 e4 77 26 a2 77 1e 09 bf e4 7b b7 d6 c1 32 7a 36 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:1b:11:57:15:11
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 d7 bb b6 e3 5a a4 8b cb 30 f8 b0 37 e2 ab 22 d0 eb dc 9c 00 b6 e0 0c 17 6e 9c 90 c9 b8 72 94 38 45 18 f9 f2 ff 00 c5 38 e4 4f 6a 7a 0b be fc 70 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 1c d9 96 63 d7 c6 42 b3 0e 49 61 15 dd 8f 3c b8 00 20 de 80 18 b4 1c 67 d3 ca da 9b 8b 57 e3 57 86 ad 98 b7 93 67 de 5d c5 b2 07 54 81 77 2e 07 91 43
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): d7 bb b6 e3 5a a4 8b cb 30 f8 b0 37 e2 ab 22 d0 eb dc 9c 00 b6 e0 0c 17 6e 9c 90 c9 b8 72 94 38
  key_iv - hexdump(len=16): 45 18 f9 f2 ff 00 c5 38 e4 4f 6a 7a 0b be fc 70
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 1c d9 96 63 d7 c6 42 b3 0e 49 61 15 dd 8f 3c b8
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 d7 bb b6 e3 5a a4 8b cb 30 f8 b0 37 e2 ab 22 d0 eb dc 9c 00 b6 e0 0c 17 6e 9c 90 c9 b8 72 94 38 45 18 f9 f2 ff 00 c5 38 e4 4f 6a 7a 0b be fc 70 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 1c d9 96 63 d7 c6 42 b3 0e 49 61 15 dd 8f 3c b8 00 20 de 80 18 b4 1c 67 d3 ca da 9b 8b 57 e3 57 86 ad 98 b7 93 67 de 5d c5 b2 07 54 81 77 2e 07 91 43
WPA: RX message 1 of Group Key Handshake from 00:1b:11:57:15:11 (ver=1)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 e5 f8 b1 18 0f 63 f0 c3 8f 5f 28 bc 2f e9 ea f7 00 00
WPA: Key negotiation completed with 00:1b:11:57:15:11 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
Removed BSSID 00:1b:11:57:15:11 from blacklist
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1b:11:57:15:11 completed (reauth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: startWhen --> 0
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_deauthenticate
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
robbingdahood@RobbingDaHood:~$ sudo wpa_supplicant -w -Dwext -i eth1 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=0
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=11):
     44 61 6e 69 65 6c 45 72 53 65 6a                  DanielErSej     
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
group: 0x8
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='DanielErSej'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:12:f0:7d:bf:97
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: External notification - portControl=Auto
Already associated with a configured network - generating associated event
Association info event
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1b:11:57:15:11
State: ASSOCIATED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1b:11:57:15:11
No keys have been configured - skip key clearing
Network configuration found for the current AP
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Associated with 00:1b:11:57:15:11
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from 00:1b:11:57:15:11
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 29 73 4e c1 13 ef e3 1c 43 93 87 6e b5 df 50 0a 6f e6 f2 e9 f5 66 c9 70 37 c4 b7 21 89 ad 21 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 29 73 4e c1 13 ef e3 1c 43 93 87 6e b5 df 50 0a 6f e6 f2 e9 f5 66 c9 70 37 c4 b7 21 89 ad 21 3c
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 29 73 4e c1 13 ef e3 1c 43 93 87 6e b5 df 50 0a 6f e6 f2 e9 f5 66 c9 70 37 c4 b7 21 89 ad 21 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1b:11:57:15:11 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): ed c6 9c a4 b0 99 0f b6 f9 aa de 7d 4b e8 9f ef 39 38 3a ce 43 c3 ca f7 66 0f 13 df e7 16 46 0f
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 ed c6 9c a4 b0 99 0f b6 f9 aa de 7d 4b e8 9f ef 39 38 3a ce 43 c3 ca f7 66 0f 13 df e7 16 46 0f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 bb 10 96 af 1c 01 a9 29 53 5a 67 d7 95 1e ad 06 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RX EAPOL from 00:1b:11:57:15:11
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 29 73 4e c1 13 ef e3 1c 43 93 87 6e b5 df 50 0a 6f e6 f2 e9 f5 66 c9 70 37 c4 b7 21 89 ad 21 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5c c1 2e 8e 7e 6f 4d 4d 10 ab 9c f0 30 16 b6 d9 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 29 73 4e c1 13 ef e3 1c 43 93 87 6e b5 df 50 0a 6f e6 f2 e9 f5 66 c9 70 37 c4 b7 21 89 ad 21 3c
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 5c c1 2e 8e 7e 6f 4d 4d 10 ab 9c f0 30 16 b6 d9
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 29 73 4e c1 13 ef e3 1c 43 93 87 6e b5 df 50 0a 6f e6 f2 e9 f5 66 c9 70 37 c4 b7 21 89 ad 21 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5c c1 2e 8e 7e 6f 4d 4d 10 ab 9c f0 30 16 b6 d9 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1b:11:57:15:11 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: No WPA/RSN IE for this AP known. Trying to get from scan results
Received 782 bytes of scan results (3 BSSes)
Scan results: 3
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: Found the current AP from updated scan results
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 66 18 08 52 a3 3e 29 69 ac 6c 5c 63 cd 7f ca 5d 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:1b:11:57:15:11
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 d7 bb b6 e3 5a a4 8b cb 30 f8 b0 37 e2 ab 22 d0 eb dc 9c 00 b6 e0 0c 17 6e 9c 90 c9 b8 72 94 38 45 18 f9 f4 ff 00 c5 38 e4 4f 6a 7a 0b be fc 70 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 57 be 0e 20 33 47 9f 44 d9 ec ae 7a f2 d0 a2 4f 00 20 5b b0 4a b3 98 89 80 d1 6e a1 cb 1a 48 6d 24 00 fc 13 7e d5 7e 9e 94 0a a3 22 60 6d b8 6b 86 03
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): d7 bb b6 e3 5a a4 8b cb 30 f8 b0 37 e2 ab 22 d0 eb dc 9c 00 b6 e0 0c 17 6e 9c 90 c9 b8 72 94 38
  key_iv - hexdump(len=16): 45 18 f9 f4 ff 00 c5 38 e4 4f 6a 7a 0b be fc 70
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 57 be 0e 20 33 47 9f 44 d9 ec ae 7a f2 d0 a2 4f
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 03 d7 bb b6 e3 5a a4 8b cb 30 f8 b0 37 e2 ab 22 d0 eb dc 9c 00 b6 e0 0c 17 6e 9c 90 c9 b8 72 94 38 45 18 f9 f4 ff 00 c5 38 e4 4f 6a 7a 0b be fc 70 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 57 be 0e 20 33 47 9f 44 d9 ec ae 7a f2 d0 a2 4f 00 20 5b b0 4a b3 98 89 80 d1 6e a1 cb 1a 48 6d 24 00 fc 13 7e d5 7e 9e 94 0a a3 22 60 6d b8 6b 86 03
WPA: RX message 1 of Group Key Handshake from 00:1b:11:57:15:11 (ver=1)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 18 00 ea c0 4b 48 8e b4 80 a5 94 08 fd d3 54 10 00 00
WPA: Key negotiation completed with 00:1b:11:57:15:11 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1b:11:57:15:11 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: startWhen --> 0

```  

It freezes in the end, and that is the problem now. 

my wpa_supplicant is:

```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=0

network={
	ssid="DanielErSej"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP
	psk=CODE

}

```

and iwconfig 

```

robbingdahood@RobbingDaHood:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"DanielErSej"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

please if you want to know more ask. 

Thank you for your time.

---

### Post by nickdbliss on 2008-07-14
Were you putting your password in ASCII code? which means not using hexadecimal version of ur password. I faced similar problem as you did. Instead of messing wpa_supplicant , i tried hexadecimal password n it worked after network restart. Infact i just had it working yesterday before it i was having open wireless.I was using simple plane password like putting nickiscool etc. It was going into loop.
From the output of #iwlist scan, it says 
Encryption key:off
 
Sorry but i guess your driver doesnt support encryption.

---

### Post by RobbingDaHood on 2008-07-14
> **nickdbliss said:**
> Were you putting your password in ASCII code? which means not using hexadecimal version of ur password. I faced similar problem as you did. Instead of messing wpa_supplicant , i tried hexadecimal password n it worked after network restart. Infact i just had it working yesterday before it i was having open wireless.I was using simple plane password like putting nickiscool etc. It was going into loop.
From the output of #iwlist scan, it says 
Encryption key:off
 
Sorry but i guess your driver doesnt support encryption.

ACII?? 

I used the 

```
wpa_passphrase your_ssid your_psk
```

to get my "psk" code, and that is WPA encryption. 

And do this page [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel) not tell me that my card and driver are able to use WPA encryption?

But I am not experienced at all with wireless so maybe I am wrong. If I am will you then tell me what to do?

---

### Post by nickdbliss on 2008-07-14
> **RobbingDaHood said:**
> ACII?? 

I used the 

```
wpa_passphrase your_ssid your_psk
```

to get my "psk" code, and that is WPA encryption. 

But I am not experienced at all with wireless so maybe I am wrong. If I am will you then tell me what to do?

Yeah that is right. That is how to get the passphrase to put when it requests u, that command converts ur ASCII code to hexadecimal.
Anyways ur iwlist scan command shows Encryption is OFF. This is what it shows on mine.
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:A2:25:FA
                    ESSID:"Home-Nick"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

It shows encryption key as on and shows extra info. I encountered the same problem as u are having when i was setting wireless on my dads laptop. I have to think what i did to have it working.

---

### Post by RobbingDaHood on 2008-07-14
> **nickdbliss said:**
> Yeah that is right. That is how to get the passphrase to put when it requests u, that command converts ur ASCII code to hexadecimal.
Anyways ur iwlist scan command shows Encryption is OFF. This is what it shows on mine.
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:A2:25:FA
                    ESSID:"Home-Nick"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

It shows encryption key as on and shows extra info. I encountered the same problem as u are having when i was setting wireless on my dads laptop. I have to think what i did to have it working.

Encryption is off on my card?

Okay I will wait.

---

### Post by nickdbliss on 2008-07-14
Ok give the output of this file.
#cat /etc/network/interfaces

---

### Post by RobbingDaHood on 2008-07-14
> **nickdbliss said:**
> Ok give the output of this file.
#cat /etc/network/interfaces

```

iface eth1 inet static 
address 192.168.0.33
netmask 255.255.255.0
wireless-essid MuttersNetværk
gateway 192.168.0.1
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant 




```

But are that not just used when you restart the net?

---

### Post by dikikx on 2008-07-14
[QUOTE=nickdbliss;5382743]Ok give the output of this file.
#cat /etc/network/interfaces[/QUOT

hows true or incorrect that the express card would not work on ubuntu OS , im using a vodafone express card (HUAWEE 3G) in my laptop sony viao, im planning to change to ubuntu os from XP, but im afraid express card would not run, sadly becuase its the only thing that i could a connection on y location. tnx ..

---

### Post by nickdbliss on 2008-07-14
> **RobbingDaHood said:**
> ```

iface eth1 inet static 
address 192.168.0.33
netmask 255.255.255.0
wireless-essid MuttersNetværk
gateway 192.168.0.1
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant 




```

But are that not just used when you restart the net?

Comment out everything with #.But leave 
auto lo
iface lo inet loopback
as such. And try connecting to ur wireless via network manager.

---

### Post by RobbingDaHood on 2008-07-14
> **nickdbliss said:**
> Comment out everything with #.But leave 
auto lo
iface lo inet loopback
as such. And try connecting to ur wireless via network manager.

That worked :D

What did i do?

---

### Post by nickdbliss on 2008-07-14
> **RobbingDaHood said:**
> That worked :D

What did i do?

That is required when u need to manually connect to internet. Otherwise network manager gets some interference. Next time instead of installing so much try to look for lil things. It works for me like that. Enjoy ur wireless now.

---

### Post by nickdbliss on 2008-07-14
Moreover i feel so many people try to put ASCII code as key when network manager asks for. Since i got experience with wireless before, so when i did it on my laptop i just used hexadecimal key and it worked without a problem.lol. How easy was that?

---

### Post by nickdbliss on 2008-07-14
Ok i forgot , But mark this thread as solved. Thanks.

---

### Post by nickdbliss on 2008-07-14
> **dikikx said:**
> [QUOTE=nickdbliss;5382743]Ok give the output of this file.
#cat /etc/network/interfaces[/QUOT

hows true or incorrect that the express card would not work on ubuntu OS , im using a vodafone express card (HUAWEE 3G) in my laptop sony viao, im planning to change to ubuntu os from XP, but im afraid express card would not run, sadly becuase its the only thing that i could a connection on y location. tnx ..

It may or may not buddy. But as far as i know the chances are not bright. Why not do a dual boot with ur xp. And see if it works. It will be better that way since we will be able to help with problems u might face using it. Like my wireless didnt worked outof the box still i managed to get it working with the help from others.

---

### Post by nickdbliss on 2008-07-14
Just out of curiosity. Can u post the output of iwlist scan now?

---

### Post by RobbingDaHood on 2008-07-27
sory I had not seen you had written anything

~$iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:11:57:15:11
                    ESSID:"DanielErSej"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=80/100  Signal level=-49 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 52ms ago

---

### Post by nickdbliss on 2008-07-27
> **RobbingDaHood said:**
> sory I had not seen you had written anything

~$iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:11:57:15:11
                    ESSID:"DanielErSej"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=80/100  Signal level=-49 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 52ms ago
Thanks buddy. Have a good day.

---

