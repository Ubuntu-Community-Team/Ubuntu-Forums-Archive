---
title: "Intel 2200BG + Cisco LEAP"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by Saibei on 2006-07-20
Hey all,

Is it possible to use the Intel 2200BG chipset to authenticate to a LEAP network? I gave it a go today using wpa_supplicant but was unable to receive a WEP key it looks like. Unfortunately I don't have the laptop on hand so I can't post the confs until tomorrow. Here's the output of [FONT="Courier New"]wpa_supplicant -Dwext -c/etc/wpa_supplicant.conf -ieth1 -dddddd[/FONT]:

```

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=5):
     67 74 6f 77 6e                                    gtown           
scan_ssid=1 (0x1)
key_mgmt: 0x8
eap methods - hexdump(len=2): 11 00
identity - hexdump_ascii(len=5):
     6a 6f 68 6e 62                                    johnb           
password - hexdump_ascii(len=8): [REMOVED]
Priority group 0
   id=0 ssid='gtown'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:13:ce:ec:97:34
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface eth1
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     67 74 6f 77 6e                                    gtown           
Scan timeout - try to get results
Received 500 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
0: 00:0d:ed:ab:78:e0 ssid='gtown' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:0d:ed:ab:78:e0 ssid='<hidden>' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:60:b3:6f:1c:0a ssid='SODAPOP' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
   selected non-WPA AP 00:0d:ed:ab:78:e0 ssid='gtown'
Trying to associate with 00:0d:ed:ab:78:e0 (SSID='gtown' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x4
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=14
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:00:00:00:00:00 into blacklist
State: ASSOCIATING -> DISCONNECTED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 2
State: DISCONNECTED -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 667 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
0: 00:0d:ed:ab:78:e0 ssid='<hidden>' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:0d:ed:ab:78:e0 ssid='gtown' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:0d:ed:ab:77:e6 ssid='<hidden>' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:60:b3:6f:1c:0a ssid='SODAPOP' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
   selected non-WPA AP 00:0d:ed:ab:78:e0 ssid='gtown'
Trying to associate with 00:0d:ed:ab:78:e0 (SSID='gtown' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x4
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=14
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:0d:ed:ab:78:e0
State: ASSOCIATING -> ASSOCIATED
Associated to a new BSS: BSSID=00:0d:ed:ab:78:e0
No keys have been configured - skip key clearing
Associated with 00:0d:ed:ab:78:e0
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=46): 01 00 00 29 01 01 00 29 01 00 6e 65 74 77 6f 72 6b 69 64 3d 67 74 6f 77 6e 2c 6e 61 73 69 64 3d 43 4f 42 31 2c 70 6f 72 74 69 64 3d 30 00
Setting authentication timeout: 70 sec 0 usec
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_PAE entering state RESTART
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request method=1 id=1
EAP: EAP entering state IDENTITY
CTRL-EVENT-EAP-STARTED EAP authentication started
EAP: EAP-Request Identity data - hexdump_ascii(len=36):
     00 6e 65 74 77 6f 72 6b 69 64 3d 67 74 6f 77 6e   _networkid=gtown
     2c 6e 61 73 69 64 3d 43 4f 42 31 2c 70 6f 72 74   ,nasid=COB1,port
     69 64 3d 30                                       id=0            
EAP: using real identity - hexdump_ascii(len=5):
     6a 6f 68 6e 62                                    johnb           
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=14): 01 00 00 0a 02 01 00 0a 01 6a 6f 68 6e 62
EAPOL: SUPP_BE entering state RECEIVE
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=46): 01 00 00 15 01 2a 00 15 11 01 00 08 e3 27 5b c2 b8 2c 92 5b 6a 6f 68 6e 62 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request method=17 id=42
EAP: EAP entering state GET_METHOD
EAP: Initialize selected EAP method (17, LEAP)
CTRL-EVENT-EAP-METHOD EAP method 17 (LEAP) selected
EAP: EAP entering state METHOD
EAP-LEAP: Processing EAP-Request
EAP-LEAP: Challenge from AP - hexdump(len=8): e3 27 5b c2 b8 2c 92 5b
EAP-LEAP: Generating Challenge Response
EAP-LEAP: Response - hexdump(len=24): 68 cb 36 16 35 30 81 22 0e 6c a1 28 2c 92 f7 5e 82 f9 2c 80 dc 03 ee ce
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=41): 01 00 00 25 02 2a 00 25 11 01 00 18 68 cb 36 16 35 30 81 22 0e 6c a1 28 2c 92 f7 5e 82 f9 2c 80 dc 03 ee ce 6a 6f 68 6e 62
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=46): 01 00 00 04 03 2a 00 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Success
EAP: EAP entering state METHOD
EAP-LEAP: Processing EAP-Success
EAP-LEAP: Challenge to AP/AS - hexdump(len=8): ab ec 29 b9 29 79 9e 33
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=25): 01 00 00 15 01 2a 00 15 11 01 00 08 ab ec 29 b9 29 79 9e 33 6a 6f 68 6e 62
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=46): 01 00 00 25 02 2b 00 25 11 01 00 18 89 a9 bc fb 47 c9 a4 12 7b 22 ca ff b8 45 56 2f 5a 6c 5d 69 e1 e1 64 86 6a 6f 68 6e 62 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Response for LEAP method=17 id=43
EAP: EAP entering state METHOD
EAP-LEAP: Processing EAP-Response
EAP-LEAP: Response from AP - hexdump(len=24): 89 a9 bc fb 47 c9 a4 12 7b 22 ca ff b8 45 56 2f 5a 6c 5d 69 e1 e1 64 86
EAP: method process -> ignore=FALSE methodState=DONE decision=UNCOND_SUCC
EAP-LEAP: pw_hash_hash - hexdump(len=16): [REMOVED]
EAP-LEAP: peer_challenge - hexdump(len=8): e3 27 5b c2 b8 2c 92 5b
EAP-LEAP: peer_response - hexdump(len=24): 68 cb 36 16 35 30 81 22 0e 6c a1 28 2c 92 f7 5e 82 f9 2c 80 dc 03 ee ce
EAP-LEAP: ap_challenge - hexdump(len=8): ab ec 29 b9 29 79 9e 33
EAP-LEAP: ap_response - hexdump(len=24): 89 a9 bc fb 47 c9 a4 12 7b 22 ca ff b8 45 56 2f 5a 6c 5d 69 e1 e1 64 86
EAP-LEAP: master key - hexdump(len=16): [REMOVED]
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAP: EAP entering state SUCCESS
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
EAPOL: SUPP_BE entering state RECEIVE
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_BE entering state IDLE
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=61): 01 03 00 39 01 00 0d 00 00 44 bf e7 25 00 51 fa f2 82 0a c2 39 02 13 3c d6 32 7e b8 4e 7f 3c 01 0c b5 5e 7a ab 12 24 49 6c 4a a4 5e 08 ae ad 7e 67 d8 02 f9 7a 22 79 e0 64 23 c5 00 fb
EAPOL: Received EAPOL-Key frame
EAPOL: KEY_RX entering state KEY_RECEIVE
EAPOL: processKey
EAPOL: RX IEEE 802.1X ver=1 type=3 len=57 EAPOL-Key: type=1 key_length=13 key_index=0x1
EAPOL: EAPOL-Key key signature verified
EAPOL: Decrypted(RC4) key - hexdump(len=13): [REMOVED]
EAPOL: Setting dynamic WEP key: broadcast keyidx 1 len 13
wpa_driver_wext_set_key: alg=1 key_idx=1 set_tx=0 seq_len=0 key_len=13
Driver did not support SIOCSIWENCODEEXT
EAPOL: Failed to set WEP key to the  driver.
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=48): 01 03 00 2c 01 00 0d 00 00 44 bf e7 25 00 52 2c 28 cb c0 ed 6a 2b b7 dc 7d 38 6a cf ab 96 98 83 32 20 e0 62 40 11 cf 78 93 78 2b d3 98 9b ab b5
EAPOL: Received EAPOL-Key frame
EAPOL: KEY_RX entering state KEY_RECEIVE
EAPOL: processKey
EAPOL: RX IEEE 802.1X ver=1 type=3 len=44 EAPOL-Key: type=1 key_length=13 key_index=0x83
EAPOL: EAPOL-Key key signature verified
EAPOL: using part of EAP keying material data encryption key - hexdump(len=13): [REMOVED]
EAPOL: Setting dynamic WEP key: unicast keyidx 3 len 13
wpa_driver_wext_set_key: alg=1 key_idx=3 set_tx=128 seq_len=0 key_len=13
Driver did not support SIOCSIWENCODEEXT
EAPOL: Failed to set WEP key to the  driver.
EAPOL: startWhen --> 0
EAPOL: authWhile --> 0
EAPOL: idleWhile --> 0
Authentication with 00:0d:ed:ab:78:e0 timed out.
Added BSSID 00:0d:ed:ab:78:e0 into blacklist
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_disassociate
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     67 74 6f 77 6e                                    gtown           
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:0d:ed:ab:78:e0 blacklist count incremented to 2
State: SCANNING -> DISCONNECTED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Scan timeout - try to get results
Received 493 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
0: 00:0d:ed:ab:78:e0 ssid='<hidden>' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
1: 00:0d:ed:ab:78:e0 ssid='gtown' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
2: 00:60:b3:6f:1c:0a ssid='SODAPOP' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No APs found - clear blacklist and try again
Removed BSSID 00:0d:ed:ab:78:e0 from blacklist (clear)
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Selecting BSS from priority group 0
0: 00:0d:ed:ab:78:e0 ssid='<hidden>' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
1: 00:0d:ed:ab:78:e0 ssid='gtown' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:60:b3:6f:1c:0a ssid='SODAPOP' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
   selected non-WPA AP 00:0d:ed:ab:78:e0 ssid='gtown'
Trying to associate with 00:0d:ed:ab:78:e0 (SSID='gtown' freq=0 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x4
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=14
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:0d:ed:ab:78:e0
State: ASSOCIATING -> ASSOCIATED
Associated to a new BSS: BSSID=00:0d:ed:ab:78:e0
No keys have been configured - skip key clearing
Associated with 00:0d:ed:ab:78:e0
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
EAP: EAP entering state INITIALIZE
EAP: deinitialize previously used EAP method (17, LEAP) at INITIALIZE
EAP: EAP entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=46): 01 00 00 29 01 01 00 29 01 00 6e 65 74 77 6f 72 6b 69 64 3d 67 74 6f 77 6e 2c 6e 61 73 69 64 3d 43 4f 42 31 2c 70 6f 72 74 69 64 3d 30 00
Setting authentication timeout: 70 sec 0 usec
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_PAE entering state RESTART
EAP: EAP entering state INITIALIZE
EAP: EAP entering state IDLE
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request method=1 id=1
EAP: EAP entering state IDENTITY
CTRL-EVENT-EAP-STARTED EAP authentication started
EAP: EAP-Request Identity data - hexdump_ascii(len=36):
     00 6e 65 74 77 6f 72 6b 69 64 3d 67 74 6f 77 6e   _networkid=gtown
     2c 6e 61 73 69 64 3d 43 4f 42 31 2c 70 6f 72 74   ,nasid=COB1,port
     69 64 3d 30                                       id=0            
EAP: using real identity - hexdump_ascii(len=5):
     6a 6f 68 6e 62                                    johnb           
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=14): 01 00 00 0a 02 01 00 0a 01 6a 6f 68 6e 62
EAPOL: SUPP_BE entering state RECEIVE
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=46): 01 00 00 15 01 2b 00 15 11 01 00 08 08 0f 66 23 67 d2 ee df 6a 6f 68 6e 62 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request method=17 id=43
EAP: EAP entering state GET_METHOD
EAP: Initialize selected EAP method (17, LEAP)
CTRL-EVENT-EAP-METHOD EAP method 17 (LEAP) selected
EAP: EAP entering state METHOD
EAP-LEAP: Processing EAP-Request
EAP-LEAP: Challenge from AP - hexdump(len=8): 08 0f 66 23 67 d2 ee df
EAP-LEAP: Generating Challenge Response
EAP-LEAP: Response - hexdump(len=24): 31 52 cf 21 2c e0 70 3b 51 cd a6 43 d7 9a e1 62 cd d8 56 55 b6 fd 93 f9
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=41): 01 00 00 25 02 2b 00 25 11 01 00 18 31 52 cf 21 2c e0 70 3b 51 cd a6 43 d7 9a e1 62 cd d8 56 55 b6 fd 93 f9 6a 6f 68 6e 62
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=46): 01 00 00 04 03 2b 00 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Success
EAP: EAP entering state METHOD
EAP-LEAP: Processing EAP-Success
EAP-LEAP: Challenge to AP/AS - hexdump(len=8): 1f 75 6e 76 7e cb be 06
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL - hexdump(len=25): 01 00 00 15 01 2b 00 15 11 01 00 08 1f 75 6e 76 7e cb be 06 6a 6f 68 6e 62
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=46): 01 00 00 25 02 2c 00 25 11 01 00 18 c3 2f cf e0 42 cb 2b 0f 26 fb 61 55 fa 76 fe 90 32 a8 ea e8 2b 49 f8 20 6a 6f 68 6e 62 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Response for LEAP method=17 id=44
EAP: EAP entering state METHOD
EAP-LEAP: Processing EAP-Response
EAP-LEAP: Response from AP - hexdump(len=24): c3 2f cf e0 42 cb 2b 0f 26 fb 61 55 fa 76 fe 90 32 a8 ea e8 2b 49 f8 20
EAP: method process -> ignore=FALSE methodState=DONE decision=UNCOND_SUCC
EAP-LEAP: pw_hash_hash - hexdump(len=16): [REMOVED]
EAP-LEAP: peer_challenge - hexdump(len=8): 08 0f 66 23 67 d2 ee df
EAP-LEAP: peer_response - hexdump(len=24): 31 52 cf 21 2c e0 70 3b 51 cd a6 43 d7 9a e1 62 cd d8 56 55 b6 fd 93 f9
EAP-LEAP: ap_challenge - hexdump(len=8): 1f 75 6e 76 7e cb be 06
EAP-LEAP: ap_response - hexdump(len=24): c3 2f cf e0 42 cb 2b 0f 26 fb 61 55 fa 76 fe 90 32 a8 ea e8 2b 49 f8 20
EAP-LEAP: master key - hexdump(len=16): [REMOVED]
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAP: EAP entering state SUCCESS
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
EAPOL: SUPP_BE entering state RECEIVE
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_BE entering state IDLE
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=61): 01 03 00 39 01 00 0d 00 00 44 bf e7 6f 00 53 80 10 72 0b 94 b9 d4 33 a7 e8 9d f8 21 ac 56 e0 01 28 97 c1 d8 ee ef 82 d5 9a 86 49 a6 a5 fe 7a 63 f2 6c a4 39 4c 89 c1 c2 cf 6c e1 14 fe
EAPOL: Received EAPOL-Key frame
EAPOL: KEY_RX entering state KEY_RECEIVE
EAPOL: processKey
EAPOL: RX IEEE 802.1X ver=1 type=3 len=57 EAPOL-Key: type=1 key_length=13 key_index=0x1
EAPOL: EAPOL-Key key signature verified
EAPOL: Decrypted(RC4) key - hexdump(len=13): [REMOVED]
EAPOL: Setting dynamic WEP key: broadcast keyidx 1 len 13
wpa_driver_wext_set_key: alg=1 key_idx=1 set_tx=0 seq_len=0 key_len=13
Driver did not support SIOCSIWENCODEEXT
EAPOL: Failed to set WEP key to the  driver.
RX EAPOL from 00:0d:ed:ab:78:e0
RX EAPOL - hexdump(len=48): 01 03 00 2c 01 00 0d 00 00 44 bf e7 6f 00 54 70 01 0c da aa d0 c6 f9 74 fa 9e 3c b3 7f e8 59 83 80 83 cc 42 b2 2c dc 5b 11 4d e3 76 b9 3a 6a 4e
EAPOL: Received EAPOL-Key frame
EAPOL: KEY_RX entering state KEY_RECEIVE
EAPOL: processKey
EAPOL: RX IEEE 802.1X ver=1 type=3 len=44 EAPOL-Key: type=1 key_length=13 key_index=0x83
EAPOL: EAPOL-Key key signature verified
EAPOL: using part of EAP keying material data encryption key - hexdump(len=13): [REMOVED]
EAPOL: Setting dynamic WEP key: unicast keyidx 3 len 13
wpa_driver_wext_set_key: alg=1 key_idx=3 set_tx=128 seq_len=0 key_len=13
Driver did not support SIOCSIWENCODEEXT
EAPOL: Failed to set WEP key to the  driver.
EAPOL: startWhen --> 0
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_deauthenticate
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
EAP: deinitialize previously used EAP method (17, LEAP) at EAP deinit
Cancelling scan request

```

Many thanks in advance!

---

### Post by skyshock21 on 2006-09-15
Don't CISCO ACS machines require that you be a part of a group mapping first before you can authenticate?  That would be my first thing to check.  If your Ubuntu laptop can't authenticate against the ACS machine, it's not going to let you in.

---

