---
title: "Wireless.  Unable to DHCP IP address, but static IP works"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by rgrashel on 2008-04-15
Hi all,

I've done a lot of homework before posting.  I have tried to get my wireless working (at my workplace) using Hardy, Gutsy, Mandriva, and PCLinuxOS 2008.  Gutsy is my preferred OS.

My machine is a Dell D620 with a built-in 3945abg interface.  I have tried this using both ipw3945 and iwlwifi.

The wpa_supplicant configuration for my workplace's access point is the following:

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1

network={
        ssid="MY-WORK-SSID"
        proto=WPA
        key_mgmt=WPA-EAP
        identity="MYDOMAIN\mylogin"
        password="mypassword"
        phase2="auth=MSCHAPV2"
        priority=1
}
```

When I do this, here is what I get when I run wpa_supplicant.  

```

EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=7 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=1396) - Flags 0x40
SSL: Need 280 bytes more input data
SSL: Building ACK (type=25 id=7 ver=0)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=10): 01 00 00 06 02 07 00 06 19 00
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=290): 01 00 01 1e 01 08 01 1e 19 00 72 69 67 68 74 20 28 63 29 20 31 39 39 37 20 4d 69 63 72 6f 73 6f 66 74 20 43 6f 72 70 2e 31 1e 30 1c 06 03 55 04 0b 13 15 4d 69 63 72 6f 73 6f 66 74 20 43 6f 72 70 6f 72 61 74 69 6f 6e 31 21 30 1f 06 03 55 04 03 13 18 4d 69 63 72 6f 73 6f 66 74 20 52 6f 6f 74 20 41 75 74 68 6f 72 69 74 79 00 4e 30 4c 31 0b 30 09 06 03 55 04 06 13 02 55 53 31 1d 30 1b 06 03 55 04 0a 13 14 53 79 6d 61 6e 74 65 63 20 43 6f 72 70 6f 72 61 74 69 6f 6e 31 1e 30 1c 06 03 55 04 03 13 15 53 79 6d 61 6e 74 65 63 20 52 6f 6f 74 20 32 30 30 35 20 43 41 00 61 30 5f 31 13 30 11 06 0a 09 92 26 89 93 f2 2c 64 01 19 16 03 63 6f 6d 31 19 30 17 06 0a 09 92 26 89 93 f2 2c 64 01 19 16 09 6d 69 63 72 6f 73 6f 66 74 31 2d 30 2b 06 03 55 04 03 13 24 4d 69 63 72 6f 73 6f 66 74 20 52 6f 6f 74 20 43 65 72 74 69 66 69 63 61 74 65 20 41 75 74 68 6f 72 69 74 79 0e 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=8 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=286) - Flags 0x00
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server hello A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server certificate A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server certificate request A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server done A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write client certificate A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write client key exchange A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write change cipher spec A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write finished A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 flush data
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read finished A
SSL: SSL_connect - want more data
SSL: 194 bytes pending from ssl_out
SSL: 194 bytes left to be sent out (of total 194 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=204): 01 00 00 c8 02 08 00 c8 19 00 16 03 01 00 07 0b 00 00 03 00 00 00 16 03 01 00 86 10 00 00 82 00 80 26 8f bf 76 a8 8f fa 21 bd d8 06 b8 a9 3a 7d da de f7 e2 53 ac c8 50 0a 7f b9 08 91 85 38 bb 39 40 ae bc a6 b1 f1 e7 26 a9 c6 53 ae 4a 6d 32 e6 ec 51 50 f3 57 30 fc 8b 9a a8 fb 9e 75 7b 38 ee 74 dc dd 13 86 e3 39 1c 62 cb 92 db 6b d7 1c e5 70 04 5f 43 cf 69 e9 19 e4 00 c4 0d e9 96 15 3a 9c 3e b0 68 b1 fa 59 36 0d e5 88 a8 77 23 dd ad d2 db 7d a2 69 eb f8 d1 df ae 1c 1b c1 23 20 79 14 03 01 00 01 01 16 03 01 00 20 c1 97 27 5d 8c f0 90 49 fe 2d 0c 23 58 db 97 1c 5a 25 66 78 2b cc 98 46 ea f0 f5 dd 73 3a bc 43
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=57): 01 00 00 35 01 09 00 35 19 80 00 00 00 2b 14 03 01 00 01 01 16 03 01 00 20 4d 05 57 1a 0d 3b e3 b8 bb 3f 27 a3 44 5c c5 a6 39 42 35 33 07 7e 81 75 ae 73 c1 76 dd f8 89 3d
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=9 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=53) - Flags 0x80
SSL: TLS Message Length: 43
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read finished A
SSL: (where=0x20 ret=0x1)
SSL: (where=0x1002 ret=0x1)
SSL: 0 bytes pending from ssl_out
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
SSL: No data to be sent out
EAP-PEAP: TLS done, proceed to Phase 2
EAP-PEAP: using label 'client EAP encryption' in key derivation
EAP-PEAP: Derived key - hexdump(len=64): [REMOVED]
SSL: Building ACK (type=25 id=9 ver=0)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=10): 01 00 00 06 02 09 00 06 19 00
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=46): 01 00 00 1c 01 0a 00 1c 19 00 17 03 01 00 11 af 52 63 a5 48 66 39 1e 41 be 71 fe 6a 1b 70 dc d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=10 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=28) - Flags 0x00
EAP-PEAP: received 22 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=1): 01
EAP-PEAP: received Phase 2: code=1 identifier=10 length=5
EAP-PEAP: Phase 2 Request: type=1
EAP: using real identity - hexdump_ascii(len=24):
     49 4e 49 54 49 41 54 45 53 59 53 54 45 4d 53 5c   MYDOMAIN\
     72 67 72 61 73 68 65 6c                           mylogin       
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=29): [REMOVED]
SSL: 46 bytes left to be sent out (of total 46 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=56): 01 00 00 34 02 0a 00 34 19 00 17 03 01 00 29 b5 38 74 d8 a7 b9 40 ed a9 75 af 9f f4 59 01 70 bc 8a 6e f7 c0 0f 2b 2a 60 a3 63 a3 9c d4 e0 9a 36 f1 07 60 60 c0 f8 32 94
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=60): 01 00 00 38 01 0b 00 38 19 00 17 03 01 00 2d 66 8b d6 75 de ac e8 bd c5 66 1e 6f c1 d6 ea 9a 5d 32 2e a2 44 51 a0 56 db 56 f2 77 7d ee b3 0c 6f ef 5f 86 b5 10 0b 9a 94 f7 1a 75 bc
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=11 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=56) - Flags 0x00
EAP-PEAP: received 50 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=29): 1a 01 0b 00 1c 10 2a dc e8 03 0e 96 5b a0 97 cb da 05 44 81 54 f4 53 43 55 4d 42 55 47
EAP-PEAP: received Phase 2: code=1 identifier=11 length=33
EAP-PEAP: Phase 2 Request: type=26
EAP-PEAP: Selected Phase 2 EAP vendor 0 method 26
EAP-MSCHAPV2: RX identifier 11 mschapv2_id 11
EAP-MSCHAPV2: Received challenge
EAP-MSCHAPV2: Authentication Servername - hexdump_ascii(len=7):
     53 43 55 4d 42 55 47                              AUTHSERVERNAME        
EAP-MSCHAPV2: Generating Challenge Response
EAP-MSCHAPV2: auth_challenge - hexdump(len=16): 2a dc e8 03 0e 96 5b a0 97 cb da 05 44 81 54 f4
EAP-MSCHAPV2: peer_challenge - hexdump(len=16): 0c c5 2b bf 66 a1 ea 7e 58 bf 98 4c e6 1f 21 3a
EAP-MSCHAPV2: username - hexdump_ascii(len=8):
     72 67 72 61 73 68 65 6c                           myloginname       
EAP-MSCHAPV2: password - hexdump_ascii(len=8): [REMOVED]
EAP-MSCHAPV2: response - hexdump(len=24): be 26 57 f0 3b c0 d7 b6 01 26 2e b7 98 96 e7 95 d6 fe f4 0b 3d 68 0f 26
EAP-MSCHAPV2: TX identifier 11 mschapv2_id 11 (response)
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=83): [REMOVED]
SSL: 100 bytes left to be sent out (of total 100 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=110): 01 00 00 6a 02 0b 00 6a 19 00 17 03 01 00 5f fd 3e 52 d6 b7 21 91 35 3c 57 9c aa a8 a5 73 b7 ee b3 d2 cf 01 56 21 49 f4 06 bf 48 8b a2 bc 36 f3 bc 25 db 8f 5a 5f 0d 53 00 a9 97 73 d4 a4 84 a6 f2 3b be 86 1c 4e 11 08 77 30 6c be 83 2c db 38 52 d6 a6 15 7a 92 08 ba 8d 96 46 be 86 ac d7 73 78 83 34 40 f7 73 fb a1 f2 59 b1 a3 a6 fc
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=78): 01 00 00 4a 01 0c 00 4a 19 00 17 03 01 00 3f f7 bf 6c bd ec be 32 2b bd c0 e6 a4 23 41 b6 bf 2a 9d f0 b0 0e be 92 0f 6e 40 96 21 e0 fc 44 d0 f2 ef ac b9 c8 58 7f 04 07 19 0a 1b 44 5c 47 d3 e8 ef 1c 0a 6d 67 76 f3 33 6e 4e af d8 9e 24
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=12 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=74) - Flags 0x00
EAP-PEAP: received 68 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=47): 1a 03 0b 00 2e 53 3d 31 36 43 34 43 39 34 35 39 43 46 31 43 42 39 39 31 43 39 42 34 46 42 44 39 37 39 46 42 45 42 37 46 38 46 36 34 34 33 44
EAP-PEAP: received Phase 2: code=1 identifier=12 length=51
EAP-PEAP: Phase 2 Request: type=26
EAP-MSCHAPV2: RX identifier 12 mschapv2_id 11
EAP-MSCHAPV2: Received success
EAP-MSCHAPV2: Success message - hexdump_ascii(len=0):
EAP-MSCHAPV2: Authentication succeeded
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=6): [REMOVED]
SSL: 23 bytes left to be sent out (of total 23 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=33): 01 00 00 1d 02 0c 00 1d 19 00 17 03 01 00 12 d6 62 11 c2 71 54 fc 88 13 29 42 6d cb 19 20 65 1f a8
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=46): 01 00 00 26 01 0d 00 26 19 00 17 03 01 00 1b e0 37 b8 b9 fe 82 40 86 4a 7a 4e fe b6 b1 ca 4c 20 e2 1b 19 17 8d 52 38 3a cb dc 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=13 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=38) - Flags 0x00
EAP-PEAP: received 32 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=11): 01 0d 00 0b 21 80 03 00 02 00 01
EAP-PEAP: received Phase 2: code=1 identifier=13 length=11
EAP-PEAP: Phase 2 Request: type=33
EAP-TLV: Received TLVs - hexdump(len=6): 80 03 00 02 00 01
EAP-TLV: Result TLV - hexdump(len=2): 00 01
EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=11): [REMOVED]
SSL: 32 bytes left to be sent out (of total 32 bytes)
EAP: method process -> ignore=FALSE methodState=DONE decision=UNCOND_SUCC
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=42): 01 00 00 26 02 0d 00 26 19 00 17 03 01 00 1b 20 8c d4 de 13 d9 89 cc db 52 c9 25 ca d4 44 c5 5c 39 68 de 23 42 16 d7 34 fc 58
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=46): 01 00 00 04 03 0e 00 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Success
EAP: Workaround for unexpected identifier field in EAP Success: reqId=14 lastId=13 (these are supposed to be same)
EAP: EAP entering state SUCCESS
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
EAPOL: SUPP_BE entering state RECEIVE
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_BE entering state IDLE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:18:ba:89:a4:40 (ver=1)
WPA: PMK from EAPOL state machines - hexdump(len=32): [REMOVED]
WPA: Renewed SNonce - hexdump(len=32): 2f 13 47 71 ce f4 1b a4 fe 6e 71 8f 51 65 d0 a6 2b fb f7 b4 78 8e d1 7b 83 3d 48 02 7a b4 28 3e
WPA: PTK derivation - A1=00:18:de:3c:fb:12 A2=00:18:ba:89:a4:40
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 2f 13 47 71 ce f4 1b a4 fe 6e 71 8f 51 65 d0 a6 2b fb f7 b4 78 8e d1 7b 83 3d 48 02 7a b4 28 3e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f5 99 2d d6 93 ec 6e 66 9c 31 fc 84 ea f1 0e 49 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b2 e9 88 ff e5 be b8 e9 b8 a7 21 c9 54 5e 20 23 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=121
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=26
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): b2 e9 88 ff e5 be b8 e9 b8 a7 21 c9 54 5e 20 23
WPA: RX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b2 e9 88 ff e5 be b8 e9 b8 a7 21 c9 54 5e 20 23 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:ba:89:a4:40 (ver=1)
WPA: IE KeyData - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7e 99 18 fd 64 04 cb 4f 9c 6f c2 80 1e f9 31 f9 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 05 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 11 51 79 f5 a2 21 8e a9 eb b4 e6 b6 6e 4b 10 9d d3 b3 c5 3d 1c 00 00 00 00 00 00 00 00 00 00 00 00 00 25 b5 be fb 74 33 0b 16 ba e6 38 ef fc 21 81 34 00 20 e5 59 25 43 50 fa 0b 8a 7a 3c c2 6b 3b c7 11 6d 8b 42 32 37 06 1a 17 68 95 2a 09 8a e0 27 f0 5a
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x3a1 (ver=1 keyidx=2 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 05
  key_nonce - hexdump(len=32): 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 11 51
  key_iv - hexdump(len=16): 79 f5 a2 21 8e a9 eb b4 e6 b6 6e 4b 10 9d d3 b3
  key_rsc - hexdump(len=8): c5 3d 1c 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 25 b5 be fb 74 33 0b 16 ba e6 38 ef fc 21 81 34
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 05 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 11 51 79 f5 a2 21 8e a9 eb b4 e6 b6 6e 4b 10 9d d3 b3 c5 3d 1c 00 00 00 00 00 00 00 00 00 00 00 00 00 25 b5 be fb 74 33 0b 16 ba e6 38 ef fc 21 81 34 00 20 e5 59 25 43 50 fa 0b 8a 7a 3c c2 6b 3b c7 11 6d 8b 42 32 37 06 1a 17 68 95 2a 09 8a e0 27 f0 5a
WPA: RX message 1 of Group Key Handshake from 00:18:ba:89:a4:40 (ver=1)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
WPA: RSC - hexdump(len=6): c5 3d 1c 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 e9 e3 21 2e fb b6 2e a7 33 1b d0 e4 62 a0 5a b3 00 00
WPA: Key negotiation completed with 00:18:ba:89:a4:40 [PTK=TKIP GTK=TKIP]
Cancelling scan request
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:18:ba:89:a4:40 completed (auth) [id=1 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: SUPP_PAE entering state AUTHENTICATED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: authWhile --> 0
EAPOL: startWhen --> 0
EAPOL: idleWhile --> 0

```

When I run wpa_supplicant, it hangs on that last "idleWhile --> 0" line.  I end up hitting CTRL-C after I wait for awhile.  I have used dhclient, et cetera, to try to get an IP address, but it just tries to DHCPDISCOVER four times, and then sleeps.  The funny thing is that if I try to assign a static IP address, it will work, but my workplace will not allow that.

Looking at this debug output from wpa_supplicant, the only thing I can think of is that the  ([UP][RUNNING][LOWER_UP]) looks different than other people's.  But I have no idea if this is true or not.

Can someone out there possibly help me?  I just need to get it to acquire an IP address.  I'd love to be able to move to Ubuntu at work, but this is preventing me from doing so.  I was even thinking of purchasing another network card if anyone could suggest one that is guaranteed to run under Linux with WPA/EAP/MSCHAPV2.

Thanks.

---

### Post by Paris Heng on 2008-04-16
> **rgrashel said:**
> Hi all,

I've done a lot of homework before posting.  I have tried to get my wireless working (at my workplace) using Hardy, Gutsy, Mandriva, and PCLinuxOS 2008.  Gutsy is my preferred OS.

My machine is a Dell D620 with a built-in 3945abg interface.  I have tried this using both ipw3945 and iwlwifi.

The wpa_supplicant configuration for my workplace's access point is the following:

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1

network={
        ssid="MY-WORK-SSID"
        proto=WPA
        key_mgmt=WPA-EAP
        identity="MYDOMAIN\mylogin"
        password="mypassword"
        phase2="auth=MSCHAPV2"
        priority=1
}
```

When I do this, here is what I get when I run wpa_supplicant.  

```

EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=7 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=1396) - Flags 0x40
SSL: Need 280 bytes more input data
SSL: Building ACK (type=25 id=7 ver=0)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=10): 01 00 00 06 02 07 00 06 19 00
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=290): 01 00 01 1e 01 08 01 1e 19 00 72 69 67 68 74 20 28 63 29 20 31 39 39 37 20 4d 69 63 72 6f 73 6f 66 74 20 43 6f 72 70 2e 31 1e 30 1c 06 03 55 04 0b 13 15 4d 69 63 72 6f 73 6f 66 74 20 43 6f 72 70 6f 72 61 74 69 6f 6e 31 21 30 1f 06 03 55 04 03 13 18 4d 69 63 72 6f 73 6f 66 74 20 52 6f 6f 74 20 41 75 74 68 6f 72 69 74 79 00 4e 30 4c 31 0b 30 09 06 03 55 04 06 13 02 55 53 31 1d 30 1b 06 03 55 04 0a 13 14 53 79 6d 61 6e 74 65 63 20 43 6f 72 70 6f 72 61 74 69 6f 6e 31 1e 30 1c 06 03 55 04 03 13 15 53 79 6d 61 6e 74 65 63 20 52 6f 6f 74 20 32 30 30 35 20 43 41 00 61 30 5f 31 13 30 11 06 0a 09 92 26 89 93 f2 2c 64 01 19 16 03 63 6f 6d 31 19 30 17 06 0a 09 92 26 89 93 f2 2c 64 01 19 16 09 6d 69 63 72 6f 73 6f 66 74 31 2d 30 2b 06 03 55 04 03 13 24 4d 69 63 72 6f 73 6f 66 74 20 52 6f 6f 74 20 43 65 72 74 69 66 69 63 61 74 65 20 41 75 74 68 6f 72 69 74 79 0e 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=8 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=286) - Flags 0x00
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server hello A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server certificate A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server certificate request A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read server done A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write client certificate A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write client key exchange A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write change cipher spec A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 write finished A
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 flush data
SSL: (where=0x1002 ret=0xffffffff)
SSL: SSL_connect:error in SSLv3 read finished A
SSL: SSL_connect - want more data
SSL: 194 bytes pending from ssl_out
SSL: 194 bytes left to be sent out (of total 194 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=204): 01 00 00 c8 02 08 00 c8 19 00 16 03 01 00 07 0b 00 00 03 00 00 00 16 03 01 00 86 10 00 00 82 00 80 26 8f bf 76 a8 8f fa 21 bd d8 06 b8 a9 3a 7d da de f7 e2 53 ac c8 50 0a 7f b9 08 91 85 38 bb 39 40 ae bc a6 b1 f1 e7 26 a9 c6 53 ae 4a 6d 32 e6 ec 51 50 f3 57 30 fc 8b 9a a8 fb 9e 75 7b 38 ee 74 dc dd 13 86 e3 39 1c 62 cb 92 db 6b d7 1c e5 70 04 5f 43 cf 69 e9 19 e4 00 c4 0d e9 96 15 3a 9c 3e b0 68 b1 fa 59 36 0d e5 88 a8 77 23 dd ad d2 db 7d a2 69 eb f8 d1 df ae 1c 1b c1 23 20 79 14 03 01 00 01 01 16 03 01 00 20 c1 97 27 5d 8c f0 90 49 fe 2d 0c 23 58 db 97 1c 5a 25 66 78 2b cc 98 46 ea f0 f5 dd 73 3a bc 43
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=57): 01 00 00 35 01 09 00 35 19 80 00 00 00 2b 14 03 01 00 01 01 16 03 01 00 20 4d 05 57 1a 0d 3b e3 b8 bb 3f 27 a3 44 5c c5 a6 39 42 35 33 07 7e 81 75 ae 73 c1 76 dd f8 89 3d
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=9 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=53) - Flags 0x80
SSL: TLS Message Length: 43
SSL: (where=0x1001 ret=0x1)
SSL: SSL_connect:SSLv3 read finished A
SSL: (where=0x20 ret=0x1)
SSL: (where=0x1002 ret=0x1)
SSL: 0 bytes pending from ssl_out
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
SSL: No data to be sent out
EAP-PEAP: TLS done, proceed to Phase 2
EAP-PEAP: using label 'client EAP encryption' in key derivation
EAP-PEAP: Derived key - hexdump(len=64): [REMOVED]
SSL: Building ACK (type=25 id=9 ver=0)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=10): 01 00 00 06 02 09 00 06 19 00
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=46): 01 00 00 1c 01 0a 00 1c 19 00 17 03 01 00 11 af 52 63 a5 48 66 39 1e 41 be 71 fe 6a 1b 70 dc d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=10 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=28) - Flags 0x00
EAP-PEAP: received 22 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=1): 01
EAP-PEAP: received Phase 2: code=1 identifier=10 length=5
EAP-PEAP: Phase 2 Request: type=1
EAP: using real identity - hexdump_ascii(len=24):
     49 4e 49 54 49 41 54 45 53 59 53 54 45 4d 53 5c   MYDOMAIN\
     72 67 72 61 73 68 65 6c                           mylogin       
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=29): [REMOVED]
SSL: 46 bytes left to be sent out (of total 46 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=56): 01 00 00 34 02 0a 00 34 19 00 17 03 01 00 29 b5 38 74 d8 a7 b9 40 ed a9 75 af 9f f4 59 01 70 bc 8a 6e f7 c0 0f 2b 2a 60 a3 63 a3 9c d4 e0 9a 36 f1 07 60 60 c0 f8 32 94
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=60): 01 00 00 38 01 0b 00 38 19 00 17 03 01 00 2d 66 8b d6 75 de ac e8 bd c5 66 1e 6f c1 d6 ea 9a 5d 32 2e a2 44 51 a0 56 db 56 f2 77 7d ee b3 0c 6f ef 5f 86 b5 10 0b 9a 94 f7 1a 75 bc
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=11 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=56) - Flags 0x00
EAP-PEAP: received 50 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=29): 1a 01 0b 00 1c 10 2a dc e8 03 0e 96 5b a0 97 cb da 05 44 81 54 f4 53 43 55 4d 42 55 47
EAP-PEAP: received Phase 2: code=1 identifier=11 length=33
EAP-PEAP: Phase 2 Request: type=26
EAP-PEAP: Selected Phase 2 EAP vendor 0 method 26
EAP-MSCHAPV2: RX identifier 11 mschapv2_id 11
EAP-MSCHAPV2: Received challenge
EAP-MSCHAPV2: Authentication Servername - hexdump_ascii(len=7):
     53 43 55 4d 42 55 47                              AUTHSERVERNAME        
EAP-MSCHAPV2: Generating Challenge Response
EAP-MSCHAPV2: auth_challenge - hexdump(len=16): 2a dc e8 03 0e 96 5b a0 97 cb da 05 44 81 54 f4
EAP-MSCHAPV2: peer_challenge - hexdump(len=16): 0c c5 2b bf 66 a1 ea 7e 58 bf 98 4c e6 1f 21 3a
EAP-MSCHAPV2: username - hexdump_ascii(len=8):
     72 67 72 61 73 68 65 6c                           myloginname       
EAP-MSCHAPV2: password - hexdump_ascii(len=8): [REMOVED]
EAP-MSCHAPV2: response - hexdump(len=24): be 26 57 f0 3b c0 d7 b6 01 26 2e b7 98 96 e7 95 d6 fe f4 0b 3d 68 0f 26
EAP-MSCHAPV2: TX identifier 11 mschapv2_id 11 (response)
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=83): [REMOVED]
SSL: 100 bytes left to be sent out (of total 100 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=110): 01 00 00 6a 02 0b 00 6a 19 00 17 03 01 00 5f fd 3e 52 d6 b7 21 91 35 3c 57 9c aa a8 a5 73 b7 ee b3 d2 cf 01 56 21 49 f4 06 bf 48 8b a2 bc 36 f3 bc 25 db 8f 5a 5f 0d 53 00 a9 97 73 d4 a4 84 a6 f2 3b be 86 1c 4e 11 08 77 30 6c be 83 2c db 38 52 d6 a6 15 7a 92 08 ba 8d 96 46 be 86 ac d7 73 78 83 34 40 f7 73 fb a1 f2 59 b1 a3 a6 fc
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=78): 01 00 00 4a 01 0c 00 4a 19 00 17 03 01 00 3f f7 bf 6c bd ec be 32 2b bd c0 e6 a4 23 41 b6 bf 2a 9d f0 b0 0e be 92 0f 6e 40 96 21 e0 fc 44 d0 f2 ef ac b9 c8 58 7f 04 07 19 0a 1b 44 5c 47 d3 e8 ef 1c 0a 6d 67 76 f3 33 6e 4e af d8 9e 24
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=12 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=74) - Flags 0x00
EAP-PEAP: received 68 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=47): 1a 03 0b 00 2e 53 3d 31 36 43 34 43 39 34 35 39 43 46 31 43 42 39 39 31 43 39 42 34 46 42 44 39 37 39 46 42 45 42 37 46 38 46 36 34 34 33 44
EAP-PEAP: received Phase 2: code=1 identifier=12 length=51
EAP-PEAP: Phase 2 Request: type=26
EAP-MSCHAPV2: RX identifier 12 mschapv2_id 11
EAP-MSCHAPV2: Received success
EAP-MSCHAPV2: Success message - hexdump_ascii(len=0):
EAP-MSCHAPV2: Authentication succeeded
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=6): [REMOVED]
SSL: 23 bytes left to be sent out (of total 23 bytes)
EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=33): 01 00 00 1d 02 0c 00 1d 19 00 17 03 01 00 12 d6 62 11 c2 71 54 fc 88 13 29 42 6d cb 19 20 65 1f a8
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=46): 01 00 00 26 01 0d 00 26 19 00 17 03 01 00 1b e0 37 b8 b9 fe 82 40 86 4a 7a 4e fe b6 b1 ca 4c 20 e2 1b 19 17 8d 52 38 3a cb dc 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Request id=13 method=25 vendor=0 vendorMethod=0
EAP: EAP entering state METHOD
SSL: Received packet(len=38) - Flags 0x00
EAP-PEAP: received 32 bytes encrypted data for Phase 2
EAP-PEAP: Decrypted Phase 2 EAP - hexdump(len=11): 01 0d 00 0b 21 80 03 00 02 00 01
EAP-PEAP: received Phase 2: code=1 identifier=13 length=11
EAP-PEAP: Phase 2 Request: type=33
EAP-TLV: Received TLVs - hexdump(len=6): 80 03 00 02 00 01
EAP-TLV: Result TLV - hexdump(len=2): 00 01
EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
EAP-PEAP: Encrypting Phase 2 data - hexdump(len=11): [REMOVED]
SSL: 32 bytes left to be sent out (of total 32 bytes)
EAP: method process -> ignore=FALSE methodState=DONE decision=UNCOND_SUCC
EAP: EAP entering state SEND_RESPONSE
EAP: EAP entering state IDLE
EAPOL: SUPP_BE entering state RESPONSE
EAPOL: txSuppRsp
TX EAPOL: dst=00:18:ba:89:a4:40
TX EAPOL - hexdump(len=42): 01 00 00 26 02 0d 00 26 19 00 17 03 01 00 1b 20 8c d4 de 13 d9 89 cc db 52 c9 25 ca d4 44 c5 5c 39 68 de 23 42 16 d7 34 fc 58
EAPOL: SUPP_BE entering state RECEIVE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=46): 01 00 00 04 03 0e 00 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Received EAP-Packet frame
EAPOL: SUPP_BE entering state REQUEST
EAPOL: getSuppRsp
EAP: EAP entering state RECEIVED
EAP: Received EAP-Success
EAP: Workaround for unexpected identifier field in EAP Success: reqId=14 lastId=13 (these are supposed to be same)
EAP: EAP entering state SUCCESS
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
EAPOL: SUPP_BE entering state RECEIVE
EAPOL: SUPP_BE entering state SUCCESS
EAPOL: SUPP_BE entering state IDLE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:18:ba:89:a4:40 (ver=1)
WPA: PMK from EAPOL state machines - hexdump(len=32): [REMOVED]
WPA: Renewed SNonce - hexdump(len=32): 2f 13 47 71 ce f4 1b a4 fe 6e 71 8f 51 65 d0 a6 2b fb f7 b4 78 8e d1 7b 83 3d 48 02 7a b4 28 3e
WPA: PTK derivation - A1=00:18:de:3c:fb:12 A2=00:18:ba:89:a4:40
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 2f 13 47 71 ce f4 1b a4 fe 6e 71 8f 51 65 d0 a6 2b fb f7 b4 78 8e d1 7b 83 3d 48 02 7a b4 28 3e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f5 99 2d d6 93 ec 6e 66 9c 31 fc 84 ea f1 0e 49 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b2 e9 88 ff e5 be b8 e9 b8 a7 21 c9 54 5e 20 23 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=121
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=26
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): b2 e9 88 ff e5 be b8 e9 b8 a7 21 c9 54 5e 20 23
WPA: RX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 c9 00 20 00 00 00 00 00 00 00 02 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 14 9a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b2 e9 88 ff e5 be b8 e9 b8 a7 21 c9 54 5e 20 23 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:18:ba:89:a4:40 (ver=1)
WPA: IE KeyData - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01 28 00
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7e 99 18 fd 64 04 cb 4f 9c 6f c2 80 1e f9 31 f9 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:18:ba:89:a4:40
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 05 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 11 51 79 f5 a2 21 8e a9 eb b4 e6 b6 6e 4b 10 9d d3 b3 c5 3d 1c 00 00 00 00 00 00 00 00 00 00 00 00 00 25 b5 be fb 74 33 0b 16 ba e6 38 ef fc 21 81 34 00 20 e5 59 25 43 50 fa 0b 8a 7a 3c c2 6b 3b c7 11 6d 8b 42 32 37 06 1a 17 68 95 2a 09 8a e0 27 f0 5a
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x3a1 (ver=1 keyidx=2 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 05
  key_nonce - hexdump(len=32): 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 11 51
  key_iv - hexdump(len=16): 79 f5 a2 21 8e a9 eb b4 e6 b6 6e 4b 10 9d d3 b3
  key_rsc - hexdump(len=8): c5 3d 1c 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 25 b5 be fb 74 33 0b 16 ba e6 38 ef fc 21 81 34
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 a1 00 20 00 00 00 00 00 00 00 05 6d 14 61 2f b1 cb 2b b2 68 e7 cd 10 3b 1c e2 cc 49 d8 02 8e 6f 77 f9 65 d6 ec 2f 67 42 e9 11 51 79 f5 a2 21 8e a9 eb b4 e6 b6 6e 4b 10 9d d3 b3 c5 3d 1c 00 00 00 00 00 00 00 00 00 00 00 00 00 25 b5 be fb 74 33 0b 16 ba e6 38 ef fc 21 81 34 00 20 e5 59 25 43 50 fa 0b 8a 7a 3c c2 6b 3b c7 11 6d 8b 42 32 37 06 1a 17 68 95 2a 09 8a e0 27 f0 5a
WPA: RX message 1 of Group Key Handshake from 00:18:ba:89:a4:40 (ver=1)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
WPA: RSC - hexdump(len=6): c5 3d 1c 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 21 00 20 00 00 00 00 00 00 00 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 e9 e3 21 2e fb b6 2e a7 33 1b d0 e4 62 a0 5a b3 00 00
WPA: Key negotiation completed with 00:18:ba:89:a4:40 [PTK=TKIP GTK=TKIP]
Cancelling scan request
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:18:ba:89:a4:40 completed (auth) [id=1 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: SUPP_PAE entering state AUTHENTICATED
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
EAPOL: authWhile --> 0
EAPOL: startWhen --> 0
EAPOL: idleWhile --> 0

```

When I run wpa_supplicant, it hangs on that last "idleWhile --> 0" line.  I end up hitting CTRL-C after I wait for awhile.  I have used dhclient, et cetera, to try to get an IP address, but it just tries to DHCPDISCOVER four times, and then sleeps.  The funny thing is that if I try to assign a static IP address, it will work, but my workplace will not allow that.

Looking at this debug output from wpa_supplicant, the only thing I can think of is that the  ([UP][RUNNING][LOWER_UP]) looks different than other people's.  But I have no idea if this is true or not.

Can someone out there possibly help me?  I just need to get it to acquire an IP address.  I'd love to be able to move to Ubuntu at work, but this is preventing me from doing so.  I was even thinking of purchasing another network card if anyone could suggest one that is guaranteed to run under Linux with WPA/EAP/MSCHAPV2.

Thanks.

Hi, have you configured the wpa_supplicant? You the Network Manager or the WICD is enough for you to connect to all type of wifi network.

---

### Post by rgrashel on 2008-04-16
> **Paris Heng said:**
> Hi, have you configured the wpa_supplicant? You the Network Manager or the WICD is enough for you to connect to all type of wifi network.

Yes, the above configuration is what I have configured for wpa_supplicant.  According to the wpa_supplicant, it associates, authenticates me, and just sits at that "idleWhile" line.  I try to dhclient at that point, and I cannot get an IP address.  But a static IP will work.

I have tried to do this using Network Manager and wicd both.  NM is broke for these purposes and does not work.  Neither does wicd.  From what I've been experiencing, NM and wicd are good for most WPA/PSK.  But if you try to do WPA1(2)/EAP/TKIP/MSCHAPV2, NM and wicd don't work that well.

Anyone else have any ideas what might be going on here?  Many thanks!

---

