---
title: "Radius / WPA / PEAP problem"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by ryanfx on 2007-09-23
Hey all,

two questions regarding the radius server I'm setting up.  I got everything configured and all and it works fine (well almost, ill get to that later) but when I connect I get a strange warning message (It DOES make a usable connection though)

```

bt ~ # wpa_supplicant -Dwext -iath0 -c/etc/wpa_supplicant.conf
Associated with 00:00:00:00:00:00
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:17:9a:47:ff:19
CTRL-EVENT-EAP-STARTED EAP authentication started
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
EAP-MSCHAPV2: Authentication succeeded
EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
WPA: Key negotiation completed with 00:17:9a:47:xx:xx [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:17:9a:47:xx:xx completed (auth) [id=0 id_str=]

```

any ideas what that OpenSSL error means?

Here is my WPA supplicant 

```

network={

ssid="You_dont_have_wireless"
scan_ssid=1
proto=WPA
key_mgmt=WPA-EAP
pairwise=TKIP
eap=PEAP
identity="ryan"
password="mypass"
phase2="auth=MSCHAPV2"

}


```

Secondly, I can connect fine the first connection, but if I disconnect, the only way to reconnect is to reset my wireless router (DI-524).  Resetting the radius server itself has no effect on whether or not I can connect, nor the client rebooting.  But once the router reboots I'm good to go again.  The following is my output on the failed connect.  This just repeats over and over and over.  Any ideas on this half?


```

bt ~ # wpa_supplicant -Dwext -iath0 -dd -c/etc/wpa_supplicant.conf
Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=22):
     59 6f 75 5f 64 6f 6e 74 5f 68 61 76 65 5f 77 69   You_dont_have_wi
     72 65 6c 65 73 73                                 reless
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x1
pairwise: 0x8
eap methods - hexdump(len=16): 00 00 00 00 19 00 00 00 00 00 00 00 00 00 00 00
identity - hexdump_ascii(len=4):
     72 79 61 6e                                       ryan
password - hexdump_ascii(len=4): [REMOVED]
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3c 4d 53 43 48 41 55 56 32            auth=MSCHAPV2
Line 13: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='You_dont_have_wireless'
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
Own MAC address: 00:11:95:68:xx:xx
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface ath0
RTM_NEWLINK: operstate=0 ifi_flags=0x1022 ()
Wireless event: cmd=0x8b06 len=8
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1023 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1023 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11023 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:17:9a:47:xx:xx
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:17:9a:47:xx:xx
No keys have been configured - skip key clearing
Network configuration found for the current AP
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 14 pairwise 8 key_mgmt 1 proto 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT 802.1X
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 01
EAPOL: External notification - portControl=Auto
Associated with 00:17:9a:47:xx:xx
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
RTM_NEWLINK: operstate=0 ifi_flags=0x11023 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1023 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:17:9a:47:xx:xx into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x11023 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:17:9a:47:xx:xx
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:17:9a:47:xx:xx
No keys have been configured - skip key clearing
Associated with 00:17:9a:47:xx:xx
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
RX EAPOL from 00:17:9a:47:xx:xx
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 0a 8c a2 df af fc 92 d3 63 97 be 9d 0b 9a 1b 97 1e d6 bc 7c e0 ba 68 cf de 15 eb fc 1a 99 2c 3b 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 70 sec 0 usec
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 0a
  key_nonce - hexdump(len=32): 8c a2 df af fc 92 d3 63 97 be 9d 0b 9a 1b 97 1e d6 bc 7c e0 ba 68 cf de 15 eb fc 1a 99 2c 3b 05
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 0a 8c a2 df af fc 92 d3 63 97 be 9d 0b 9a 1b 97 1e d6 bc 7c e0 ba 68 cf de 15 eb fc 1a 99 2c 3b 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:17:9a:47:ff:19 (ver=1)
WPA: Failed to get master session key from EAPOL state machines
WPA: Key handshake aborted
RTM_NEWLINK: operstate=0 ifi_flags=0x11023 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RX EAPOL from 00:17:9a:47:xx:xx
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 0b d7 bd 7d 9c 38 8d 93 de e5 68 0a e4 e9 1c 3f ee ca f7 cf 6a 89 58 ff 70 65 07 dd eb 62 45 23 97 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
EAPOL: Ignoring WPA EAPOL-Key frame in EAPOL state machines
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 0b
  key_nonce - hexdump(len=32): d7 bd 7d 9c 38 8d 93 de e5 68 0a e4 e9 1c 3f ee ca f7 cf 6a 89 58 ff 70 65 07 dd eb 62 45 23 97
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 0b d7 bd 7d 9c 38 8d 93 de e5 68 0a e4 e9 1c 3f ee ca f7 cf 6a 89 58 ff 70 65 07 dd eb 62 45 23 97 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:17:9a:47:xx:xx (ver=1)
WPA: Failed to get master session key from EAPOL state machines
WPA: Key handshake aborted

```

---

### Post by ryanfx on 2007-09-23
bump for the day crew!

---

### Post by wirelessmonkey on 2007-09-24
OK... For the SSL error, I'm not absolutely sure but I think if you attach -dd to your wpasupp startup, you'll see that the error is resolved shortly thereafter, as you need to have a full handshake for the tls connection to complete.

The second problem is probably due to a bug or misconfiguration on the switch.  When you attempt to reauthenticate, the switch is not resetting the .1x status of the port, hence the authentication failure.  I had this problem with a D-Link VOIP switch some time ago. Unfortunately, I don't have access to any D-Link products, so I can't double check for you.

---

