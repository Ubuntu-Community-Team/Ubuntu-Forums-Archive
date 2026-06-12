---
title: "ndiswrapper + wpa_supplicant + broadcom BCM4318 not working?!"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by IndieRockSteve on 2007-09-06
I've followed all the instructions on this forum for getting this to work but wpa_supplicant continuously blacklists my access point. if I use the bcm43xx driver it works but I can connect any faster than 11M or the driver seems to freak out and stop working. This worked for a while but then it stopped working a few days ago, which is the really weird part...

# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)


wpa_supplicant.conf
> 
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
        ssid="AthertonHouse"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        #psk="6178675309"
        psk=b3c5d703989e6ed4191a4b8b83c8eb30345f4f674c2a02fd01c71107f248db7a
}


```

# wpa_supplicant -ddd -Dwext -ieth1 -c/etc/wpa_supplicant.conf
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=1
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=13):
     41 74 68 65 72 74 6f 6e 48 6f 75 73 65            AthertonHouse
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='AthertonHouse'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=21 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:90:4b:f1:6a:77
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
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=13):
     41 74 68 65 72 74 6f 6e 48 6f 75 73 65            AthertonHouse
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 1471 bytes of scan results (6 BSSes)
Scan results: 6
Selecting BSS from priority group 0
0: 00:09:5b:dc:d8:34 ssid='AthertonHouse' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:09:5b:dc:d8:34 (SSID='AthertonHouse' freq=2447 MHz)
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
Wireless event: cmd=0x8b1a len=21
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=92
AssocReq IE wireless event - hexdump(len=84): 00 0d 41 74 68 65 72 74 6f 6e 48 6f 75 73 65 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 06 00 40 96 01 01 00 dd 09 00 10 18 02 00 10 00 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:09:5b:dc:d8:34
Association info event
req_ies - hexdump(len=84): 00 0d 41 74 68 65 72 74 6f 6e 48 6f 75 73 65 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 06 00 40 96 01 01 00 dd 09 00 10 18 02 00 10 00 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:09:5b:dc:d8:34
No keys have been configured - skip key clearing
Associated with 00:09:5b:dc:d8:34
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 5e 8b 8a b8 7c a0 4b de 6d 7b cb c3 31 37 3b 67 1e de 02 b2 04 cf 61 b2 37 cb e6 7a 66 8b 4f 2f 3a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 5e
  key_nonce - hexdump(len=32): 8b 8a b8 7c a0 4b de 6d 7b cb c3 31 37 3b 67 1e de 02 b2 04 cf 61 b2 37 cb e6 7a 66 8b 4f 2f 3a
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 5e 8b 8a b8 7c a0 4b de 6d 7b cb c3 31 37 3b 67 1e de 02 b2 04 cf 61 b2 37 cb e6 7a 66 8b 4f 2f 3a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:09:5b:dc:d8:34 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 93 73 d1 01 7a b7 04 65 83 b0 94 d1 32 e3 6c 60 46 bd 25 8d 40 e1 9f 09 c1 54 e9 ae fa fd 8c c3
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 09 00 20 00 00 00 00 00 00 37 5e 93 73 d1 01 7a b7 04 65 83 b0 94 d1 32 e3 6c 60 46 bd 25 8d 40 e1 9f 09 c1 54 e9 ae fa fd 8c c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f4 ef 07 15 c9 0e 1d 9d 0c 57 3e 43 45 ff f6 a2 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 60 8b 8a b8 7c a0 4b de 6d 7b cb c3 31 37 3b 67 1e de 02 b2 04 cf 61 b2 37 cb e6 7a 66 8b 4f 2f 3a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b6 24 6d 0e 32 ca 69 00 53 2e b8 6c 25 f6 a7 78 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 60
  key_nonce - hexdump(len=32): 8b 8a b8 7c a0 4b de 6d 7b cb c3 31 37 3b 67 1e de 02 b2 04 cf 61 b2 37 cb e6 7a 66 8b 4f 2f 3a
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): b6 24 6d 0e 32 ca 69 00 53 2e b8 6c 25 f6 a7 78
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 60 8b 8a b8 7c a0 4b de 6d 7b cb c3 31 37 3b 67 1e de 02 b2 04 cf 61 b2 37 cb e6 7a 66 8b 4f 2f 3a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b6 24 6d 0e 32 ca 69 00 53 2e b8 6c 25 f6 a7 78 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 63 87 9c fb 3a 26 59 24 56 24 4d 88 4d 6b 11 d7 a5 43 5e 84 06 cc 8b ac 7f f7 e7 5d ad 53 8c 69 b3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 63
  key_nonce - hexdump(len=32): 87 9c fb 3a 26 59 24 56 24 4d 88 4d 6b 11 d7 a5 43 5e 84 06 cc 8b ac 7f f7 e7 5d ad 53 8c 69 b3
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 63 87 9c fb 3a 26 59 24 56 24 4d 88 4d 6b 11 d7 a5 43 5e 84 06 cc 8b ac 7f f7 e7 5d ad 53 8c 69 b3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:09:5b:dc:d8:34 (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 09 00 20 00 00 00 00 00 00 37 63 93 73 d1 01 7a b7 04 65 83 b0 94 d1 32 e3 6c 60 46 bd 25 8d 40 e1 9f 09 c1 54 e9 ae fa fd 8c c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 d4 7d dd 29 86 f3 88 69 cc bc d8 76 c7 3f 53 12 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 64 87 9c fb 3a 26 59 24 56 24 4d 88 4d 6b 11 d7 a5 43 5e 84 06 cc 8b ac 7f f7 e7 5d ad 53 8c 69 b3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 21 27 5d e2 4e 1d af f2 7b c7 d9 e3 9b d6 f2 b7 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 64
  key_nonce - hexdump(len=32): 87 9c fb 3a 26 59 24 56 24 4d 88 4d 6b 11 d7 a5 43 5e 84 06 cc 8b ac 7f f7 e7 5d ad 53 8c 69 b3
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 21 27 5d e2 4e 1d af f2 7b c7 d9 e3 9b d6 f2 b7
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 64 87 9c fb 3a 26 59 24 56 24 4d 88 4d 6b 11 d7 a5 43 5e 84 06 cc 8b ac 7f f7 e7 5d ad 53 8c 69 b3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 21 27 5d e2 4e 1d af f2 7b c7 d9 e3 9b d6 f2 b7 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 68 05 fc fe f0 80 d2 ac 99 7c 08 08 a9 d9 98 a0 af b9 28 60 e0 95 d5 10 13 98 76 16 b2 2f 60 05 99 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 68
  key_nonce - hexdump(len=32): 05 fc fe f0 80 d2 ac 99 7c 08 08 a9 d9 98 a0 af b9 28 60 e0 95 d5 10 13 98 76 16 b2 2f 60 05 99
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 68 05 fc fe f0 80 d2 ac 99 7c 08 08 a9 d9 98 a0 af b9 28 60 e0 95 d5 10 13 98 76 16 b2 2f 60 05 99 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:09:5b:dc:d8:34 (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 09 00 20 00 00 00 00 00 00 37 68 93 73 d1 01 7a b7 04 65 83 b0 94 d1 32 e3 6c 60 46 bd 25 8d 40 e1 9f 09 c1 54 e9 ae fa fd 8c c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 48 14 b9 1a b9 97 4f bd 0c 3d d7 b0 80 d4 68 b6 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 69 05 fc fe f0 80 d2 ac 99 7c 08 08 a9 d9 98 a0 af b9 28 60 e0 95 d5 10 13 98 76 16 b2 2f 60 05 99 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2b 22 b9 5f b1 53 6f 84 56 e1 f9 d8 33 cf 40 7c 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 69
  key_nonce - hexdump(len=32): 05 fc fe f0 80 d2 ac 99 7c 08 08 a9 d9 98 a0 af b9 28 60 e0 95 d5 10 13 98 76 16 b2 2f 60 05 99
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 2b 22 b9 5f b1 53 6f 84 56 e1 f9 d8 33 cf 40 7c
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 69 05 fc fe f0 80 d2 ac 99 7c 08 08 a9 d9 98 a0 af b9 28 60 e0 95 d5 10 13 98 76 16 b2 2f 60 05 99 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2b 22 b9 5f b1 53 6f 84 56 e1 f9 d8 33 cf 40 7c 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 6d 6f db 2c 6b d0 28 6c 0e 12 0d 16 a9 f0 aa 09 74 45 e7 51 20 35 96 46 97 f6 1c bc 39 97 2c 59 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 6d
  key_nonce - hexdump(len=32): 6f db 2c 6b d0 28 6c 0e 12 0d 16 a9 f0 aa 09 74 45 e7 51 20 35 96 46 97 f6 1c bc 39 97 2c 59 91
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 6d 6f db 2c 6b d0 28 6c 0e 12 0d 16 a9 f0 aa 09 74 45 e7 51 20 35 96 46 97 f6 1c bc 39 97 2c 59 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:09:5b:dc:d8:34 (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 09 00 20 00 00 00 00 00 00 37 6d 93 73 d1 01 7a b7 04 65 83 b0 94 d1 32 e3 6c 60 46 bd 25 8d 40 e1 9f 09 c1 54 e9 ae fa fd 8c c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 8f 16 4b cc 42 38 01 d6 d2 d6 d6 5f d7 39 8e d0 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 6e 6f db 2c 6b d0 28 6c 0e 12 0d 16 a9 f0 aa 09 74 45 e7 51 20 35 96 46 97 f6 1c bc 39 97 2c 59 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 1a 76 be 81 5c 21 7f ee 27 f5 9a 8c e1 98 ae 57 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 6e
  key_nonce - hexdump(len=32): 6f db 2c 6b d0 28 6c 0e 12 0d 16 a9 f0 aa 09 74 45 e7 51 20 35 96 46 97 f6 1c bc 39 97 2c 59 91
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 1a 76 be 81 5c 21 7f ee 27 f5 9a 8c e1 98 ae 57
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 6e 6f db 2c 6b d0 28 6c 0e 12 0d 16 a9 f0 aa 09 74 45 e7 51 20 35 96 46 97 f6 1c bc 39 97 2c 59 91 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 1a 76 be 81 5c 21 7f ee 27 f5 9a 8c e1 98 ae 57 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 72 be 81 f1 42 a8 40 ba 35 43 46 c6 bc 4e d8 f7 11 78 35 e3 98 26 16 93 59 27 b7 a3 0a b1 04 dc a5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 72
  key_nonce - hexdump(len=32): be 81 f1 42 a8 40 ba 35 43 46 c6 bc 4e d8 f7 11 78 35 e3 98 26 16 93 59 27 b7 a3 0a b1 04 dc a5
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 72 be 81 f1 42 a8 40 ba 35 43 46 c6 bc 4e d8 f7 11 78 35 e3 98 26 16 93 59 27 b7 a3 0a b1 04 dc a5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:09:5b:dc:d8:34 (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 09 00 20 00 00 00 00 00 00 37 72 93 73 d1 01 7a b7 04 65 83 b0 94 d1 32 e3 6c 60 46 bd 25 8d 40 e1 9f 09 c1 54 e9 ae fa fd 8c c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2e 7e 7d 03 0a 37 0e 22 9a c6 ac bf a9 3b 24 e1 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 73 be 81 f1 42 a8 40 ba 35 43 46 c6 bc 4e d8 f7 11 78 35 e3 98 26 16 93 59 27 b7 a3 0a b1 04 dc a5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a5 2c bf ab 55 53 57 1c 97 1d 0b 59 a9 82 2f 85 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 73
  key_nonce - hexdump(len=32): be 81 f1 42 a8 40 ba 35 43 46 c6 bc 4e d8 f7 11 78 35 e3 98 26 16 93 59 27 b7 a3 0a b1 04 dc a5
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): a5 2c bf ab 55 53 57 1c 97 1d 0b 59 a9 82 2f 85
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 73 be 81 f1 42 a8 40 ba 35 43 46 c6 bc 4e d8 f7 11 78 35 e3 98 26 16 93 59 27 b7 a3 0a b1 04 dc a5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a5 2c bf ab 55 53 57 1c 97 1d 0b 59 a9 82 2f 85 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 77 f8 49 33 d1 85 76 c7 b3 bb f4 69 53 bf 68 6e 8a f1 c5 20 e1 d0 99 9a cb 90 7b 5d 77 52 35 a2 c8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 77
  key_nonce - hexdump(len=32): f8 49 33 d1 85 76 c7 b3 bb f4 69 53 bf 68 6e 8a f1 c5 20 e1 d0 99 9a cb 90 7b 5d 77 52 35 a2 c8
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 77 f8 49 33 d1 85 76 c7 b3 bb f4 69 53 bf 68 6e 8a f1 c5 20 e1 d0 99 9a cb 90 7b 5d 77 52 35 a2 c8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:09:5b:dc:d8:34 (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 09 00 20 00 00 00 00 00 00 37 77 93 73 d1 01 7a b7 04 65 83 b0 94 d1 32 e3 6c 60 46 bd 25 8d 40 e1 9f 09 c1 54 e9 ae fa fd 8c c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5d 18 f8 3a 15 c1 10 5b cb 82 6a d7 1e 70 f4 78 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 78 f8 49 33 d1 85 76 c7 b3 bb f4 69 53 bf 68 6e 8a f1 c5 20 e1 d0 99 9a cb 90 7b 5d 77 52 35 a2 c8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 72 88 bd fe b9 22 77 0f 0b 6c 92 76 05 0b 18 04 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 78
  key_nonce - hexdump(len=32): f8 49 33 d1 85 76 c7 b3 bb f4 69 53 bf 68 6e 8a f1 c5 20 e1 d0 99 9a cb 90 7b 5d 77 52 35 a2 c8
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 72 88 bd fe b9 22 77 0f 0b 6c 92 76 05 0b 18 04
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 37 78 f8 49 33 d1 85 76 c7 b3 bb f4 69 53 bf 68 6e 8a f1 c5 20 e1 d0 99 9a cb 90 7b 5d 77 52 35 a2 c8 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 72 88 bd fe b9 22 77 0f 0b 6c 92 76 05 0b 18 04 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Invalid EAPOL-Key MIC when using TPTK - ignoring TPTK
WPA: Could not verify EAPOL-Key MIC - dropping packet
Authentication with 00:09:5b:dc:d8:34 timed out.
Added BSSID 00:09:5b:dc:d8:34 into blacklist
State: 4WAY_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_disassociate
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:09:5b:dc:d8:34 blacklist count incremented to 2
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
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
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=21
Scan timeout - try to get results
Received 1510 bytes of scan results (6 BSSes)
Scan results: 6
Selecting BSS from priority group 0
0: 00:09:5b:dc:d8:34 ssid='AthertonHouse' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - blacklisted
1: 00:11:24:a7:06:3f ssid='Apple Network a7063f' wpa_ie_len=26 rsn_ie_len=26 caps=0x11
   skip - SSID mismatch
2: 00:12:0e:1b:07:a7 ssid='HARLEY' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:17:31:e4:c2:e0 ssid='The Kana Network' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:14:bf:18:80:3e ssid='dd-wrt' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
5: 00:14:6c:00:cc:b2 ssid='NETGEAR' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
No APs found - clear blacklist and try again
Removed BSSID 00:09:5b:dc:d8:34 from blacklist (clear)
Selecting BSS from priority group 0
0: 00:09:5b:dc:d8:34 ssid='AthertonHouse' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:09:5b:dc:d8:34 (SSID='AthertonHouse' freq=2447 MHz)
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
State: DISCONNECTED -> ASSOCIATING
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
Wireless event: cmd=0x8b1a len=21
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from 00:09:5b:dc:d8:34
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 7c 33 28 db 3a 56 1d 25 53 73 2a 0c e7 ba 57 0e 49 de df 0e 5b 08 54 5d 84 e1 73 38 53 7c 3f dd ce 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 37 7c
  key_nonce - hexdump(len=32): 33 28 db 3a 56 1d 25 53 73 2a 0c e7 ba 57 0e 49 de df 0e 5b 08 54 5d 84 e1 73 38 53 7c 3f dd ce
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 37 7c 33 28 db 3a 56 1d 25 53 73 2a 0c e7 ba 57 0e 49 de df 0e 5b 08 54 5d 84 e1 73 38 53 7c 3f dd ce 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATING -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:09:5b:dc:d8:34 (ver=1)
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 37 7c 93 73 d1 01 7a b7 04 65 83 b0 94 d1 32 e3 6c 60 46 bd 25 8d 40 e1 9f 09 c1 54 e9 ae fa fd 8c c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 79 9a ea 9d b3 59 a0 21 0d 2f ab af db 48 bb 13 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=92
AssocReq IE wireless event - hexdump(len=84): 00 0d 41 74 68 65 72 74 6f 6e 48 6f 75 73 65 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 06 00 40 96 01 01 00 dd 09 00 10 18 02 00 10 00 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:09:5b:dc:d8:34
Association info event
req_ies - hexdump(len=84): 00 0d 41 74 68 65 72 74 6f 6e 48 6f 75 73 65 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 06 00 40 96 01 01 00 dd 09 00 10 18 02 00 10 00 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 0c 00
State: 4WAY_HANDSHAKE -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:09:5b:dc:d8:34
No keys have been configured - skip key clearing
Associated with 00:09:5b:dc:d8:34
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface eth1
State: ASSOCIATED -> DISCONNECTED
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
WEXT: Operstate: linkmode=0, operstate=6
Cancelling scan request

```

---

### Post by belias on 2007-09-06
don't know if this would help you. i found it on my long journey to fix my own problem..seems easy though.
[http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm](http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm)
any regards, good luck.

---

### Post by IndieRockSteve on 2007-09-11
I've come to the conclusion ndiswrapper just can't handle WPA or WPA2 with this chipset. I'm using the bcm43xx module. it works, but only just.

oh well

---

### Post by kevdog on 2007-09-12
You are talking to a guy using ndiswrapper/bcmwl5 driver with WPA2.

Just for point of reference are you connecting to WPA1 or WPA2

Just for kicks lets just go with WPA1 for right now.

Your wpa_supplicant.conf file should be the following:
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
ssid="AthertonHouse"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
group=TKIP
psk=b3c5d703989e6ed4191a4b8b83c8eb30345f4f674c2a02 fd01c71107f248db7a
}

Im assuming the psk has been generated appropriately.

Are you sure your interface is eth1 since ndiswrapper usually assumes an interface on wlan0??

You may need to modify your /etc/iftab file to make sure.

Can you list the full command line commands you are using attempting to bring up the connection manually??

Can you connect to an unencrypted network to confirm everything is right as far as driver setup, etc?

---

### Post by kevdog on 2007-09-12
Can you also post 
iwlist scan

---

