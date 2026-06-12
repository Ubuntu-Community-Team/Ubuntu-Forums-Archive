---
title: "[SOLVED] Wireless losing connection"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by Juzz on 2008-11-28
Ever since I upgraded to intrepid I have been unable to connect to my WPA encrypted network - and I am now tired of having to use the cable to make a desktop out of my laptop.

Here's debud output from wpa_supplicant:

```
sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -d

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Priority group 5
   id=0 ssid='Juzz2'
Priority group 4
   id=1 ssid='bqvj7v7p'
Priority group 3
   id=2 ssid='Juzz'
Priority group 1
   id=3 ssid=''
Initializing interface (2) 'eth1'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:19:d2:63:a5:f9
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface eth1
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=5):
     4a 75 7a 7a 32                                    Juzz2           
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 5
Try to find WPA-enabled AP
Try to find non-WPA AP
Selecting BSS from priority group 4
Try to find WPA-enabled AP
Try to find non-WPA AP
Selecting BSS from priority group 3
Try to find WPA-enabled AP
Try to find non-WPA AP
Selecting BSS from priority group 1
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b19 len=8
Received 4092 bytes of scan results (16 BSSes)
CTRL-EVENT-SCAN-RESULTS 
Selecting BSS from priority group 5
Try to find WPA-enabled AP
0: 00:22:15:00:02:78 ssid='Juzz2' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:22:15:00:02:78 ssid='Juzz2'
Try to find non-WPA AP
Trying to associate with 00:22:15:00:02:78 (SSID='Juzz2' freq=2457 MHz)
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
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8c02 len=177
Association info event
req_ies - hexdump(len=47): 00 05 4a 75 7a 7a 32 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 02 f0
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:22:15:00:02:78
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:22:15:00:02:78
No keys have been configured - skip key clearing
Associated with 00:22:15:00:02:78
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX EAPOL from 00:22:15:00:02:78
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 15
  key_nonce - hexdump(len=32): f0 e6 60 df 6d 88 07 62 c4 c9 15 53 e4 6d 2f 04 1a 3d 5e d5 07 33 3b e5 7f d4 41 17 85 cb 4c 63
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:22:15:00:02:78 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 0a ef f8 69 76 4e c4 62 7b 24 24 91 06 68 8d 12 32 ff d1 09 e5 a0 02 78 dc 1f f4 dc b4 c6 b9 52
WPA: PTK derivation - A1=00:19:d2:63:a5:f9 A2=00:22:15:00:02:78
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:22:15:00:02:78
IEEE 802.1X RX: version=1 type=3 length=121
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=26
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 16
  key_nonce - hexdump(len=32): f0 e6 60 df 6d 88 07 62 c4 c9 15 53 e4 6d 2f 04 1a 3d 5e d5 07 33 3b e5 7f d4 41 17 85 cb 4c 63
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 4c 22 1f 2c 21 e4 69 00 e1 63 65 8b 5b 0c 1e 13
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:22:15:00:02:78 (ver=1)
WPA: IE KeyData - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:22:15:00:02:78
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
  key_info 0x391 (ver=1 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=32 key_data_length=32
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 17
  key_nonce - hexdump(len=32): f0 e6 60 df 6d 88 07 62 c4 c9 15 53 e4 6d 2f 04 1a 3d 5e d5 07 33 3b e5 7f d4 41 17 85 cb 4c 57
  key_iv - hexdump(len=16): 1a 3d 5e d5 07 33 3b e5 7f d4 41 17 85 cb 4c 64
  key_rsc - hexdump(len=8): 49 9a 01 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): e6 b8 34 6b 74 25 ed c4 99 82 54 aa 7f 59 ea 28
WPA: RX message 1 of Group Key Handshake from 00:22:15:00:02:78 (ver=1)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 49 9a 01 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: Key negotiation completed with 00:22:15:00:02:78 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:22:15:00:02:78 completed (auth) [id=0 id_str=location1]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=1 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
l2_packet_receive - recvfrom: Network is down
CTRL_IFACE monitor attached - hexdump(len=22): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 33 37 30 35 2d 30 00
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RTM_NEWLINK: operstate=1 ifi_flags=0x11042 ([RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b19 len=8
Received 275 bytes of scan results (1 BSSes)
CTRL-EVENT-SCAN-RESULTS 
CTRL_IFACE monitor send - hexdump(len=22): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 33 37 30 35 2d 30 00
Selecting BSS from priority group 5
Try to find WPA-enabled AP
0: 00:22:15:00:02:78 ssid='Juzz2' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:22:15:00:02:78 ssid='Juzz2'
Try to find non-WPA AP
Already associated with the selected AP.
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
RX ctrl_iface - hexdump_ascii(len=4):
     50 49 4e 47                                       PING            
CTRL_IFACE monitor detached - hexdump(len=22): 2f 74 6d 70 2f 77 70 61 5f 63 74 72 6c 5f 31 33 37 30 35 2d 30 00

```

Here's the corresponding part of my wpa_supplicant.conf:

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        # Folehaven
        id_str="location1"
        ssid="Juzz2"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=xxx
        pairwise=TKIP
        group=TKIP
        priority=5
}
```
Can anyone help me getting rid of the cable?

---

### Post by Juzz on 2008-11-28
I solved this using this suggestion:

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

From this post (I replaced hardy with intrepid)
[http://ubuntuforums.org/showpost.php?p=5276990&postcount=43](http://ubuntuforums.org/showpost.php?p=5276990&postcount=43)

Thanks to chili555

---

