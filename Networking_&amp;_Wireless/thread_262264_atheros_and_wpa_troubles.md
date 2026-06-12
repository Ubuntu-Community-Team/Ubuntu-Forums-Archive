---
title: "atheros and wpa troubles"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by sharkcohen on 2006-09-21
I have an atheros based card and cannot get wpa to work.  I've updated madwifi to madwifi-ng, and I've installed the latest wpa_supplicant.

Here is my wpa_supplicant.conf:

```

ctrl_interface=/var/run/wpa_supplicant

network={
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP

        ssid="SHARKNET"
        #psk="carcharodon"
        psk=33f597be96efc4b8693f9c88544c0030937e00c13cc321c6f898049d9176d856

        priority=2
}

```

Here's my output from wpa_supplicant:

```

root@sharkdesk:/usr/local/sbin# ./wpa_supplicant -dd -K -t -i ath0 -D madwifi -c /etc/wpa_supplicant.conf
Sep 21 10:25:11.446929: Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A'
Sep 21 10:25:11.447185: Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Sep 21 10:25:11.447287: Reading configuration file '/etc/wpa_supplicant.conf'
Sep 21 10:25:11.447359: ctrl_interface='/var/run/wpa_supplicant'
Sep 21 10:25:11.447381: Line: 7 - start of a new network block
Sep 21 10:25:11.447403: proto: 0x1
Sep 21 10:25:11.447421: key_mgmt: 0x2
Sep 21 10:25:11.447442: pairwise: 0x8
Sep 21 10:25:11.447467: group: 0x8
Sep 21 10:25:11.447487: ssid - hexdump_ascii(len=8):
     53 48 41 52 4b 4e 45 54                           SHARKNET        
Sep 21 10:25:11.447793: PSK - hexdump(len=32): 33 f5 97 be 96 ef c4 b8 69 3f 9c 88 54 4c 00 30 93 7e 00 c1 3c c3 21 c6 f8 98 04 9d 91 76 d8 56
Sep 21 10:25:11.447854: priority=2 (0x2)
Sep 21 10:25:11.447938: Priority group 2
Sep 21 10:25:11.447963:    id=0 ssid='SHARKNET'
Sep 21 10:25:11.447984: Initializing interface (2) 'ath0'
Sep 21 10:25:11.450136: SIOCGIWRANGE: WE(compiled)=19 WE(source)=13 enc_capa=0xf
Sep 21 10:25:11.450214:   capabilities: key_mgmt 0xf enc 0xf
Sep 21 10:25:11.471842: Own MAC address: 00:14:6c:89:40:a9
Sep 21 10:25:11.471935: wpa_driver_madwifi_del_key: keyidx=0
Sep 21 10:25:11.471987: wpa_driver_madwifi_del_key: keyidx=1
Sep 21 10:25:11.472007: wpa_driver_madwifi_del_key: keyidx=2
Sep 21 10:25:11.472026: wpa_driver_madwifi_del_key: keyidx=3
Sep 21 10:25:11.472045: wpa_driver_madwifi_set_countermeasures: enabled=0
Sep 21 10:25:11.472066: wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Sep 21 10:25:11.472129: Setting scan request: 0 sec 100000 usec
Sep 21 10:25:11.472239: Added interface ath0
Sep 21 10:25:11.472318: Wireless event: cmd=0x8b06 len=8
Sep 21 10:25:11.472362: Ignore event for foreign ifindex 2
Sep 21 10:25:11.472392: RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
Sep 21 10:25:11.472426: RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
Sep 21 10:25:11.575826: State: DISCONNECTED -> SCANNING
Sep 21 10:25:11.575915: Starting AP scan (broadcast SSID)
Sep 21 10:25:11.683520: Wireless event: cmd=0x8b1a len=8
Sep 21 10:25:13.391664: Wireless event: cmd=0x8b19 len=8
Sep 21 10:25:13.392318: Received 3986 bytes of scan results (19 BSSes)
Sep 21 10:25:13.392360: Scan results: 19
Sep 21 10:25:13.392382: Selecting BSS from priority group 2
Sep 21 10:25:13.392403: 0: 00:18:4d:4c:e0:6c ssid='SHARKNET' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
Sep 21 10:25:13.392434:    selected based on WPA IE
Sep 21 10:25:13.392462: Trying to associate with 00:18:4d:4c:e0:6c (SSID='SHARKNET' freq=2462 MHz)
Sep 21 10:25:13.392482: Cancelling scan request
Sep 21 10:25:13.392499: WPA: clearing own WPA/RSN IE
Sep 21 10:25:13.392514: Automatic auth_alg selection: 0x1
Sep 21 10:25:13.392547: WPA: using IEEE 802.11i/D3.0
Sep 21 10:25:13.392564: WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
Sep 21 10:25:13.392581: WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 10:25:13.392608: WPA: clearing AP RSN IE
Sep 21 10:25:13.392624: WPA: using GTK TKIP
Sep 21 10:25:13.392644: WPA: using PTK TKIP
Sep 21 10:25:13.392660: WPA: using KEY_MGMT WPA-PSK
Sep 21 10:25:13.392677: WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 10:25:13.392706: No keys have been configured - skip key clearing
Sep 21 10:25:13.392722: wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Sep 21 10:25:13.392741: State: SCANNING -> ASSOCIATING
Sep 21 10:25:13.392757: wpa_driver_madwifi_associate
ioctl[unknown???]: Invalid argument
Sep 21 10:25:13.393115: Association request to the driver failed
Sep 21 10:25:13.393140: Setting authentication timeout: 5 sec 0 usec
Sep 21 10:25:13.393185: Wireless event: cmd=0x8b1a len=17
Sep 21 10:25:13.398056: Wireless event: cmd=0x8b15 len=20
Sep 21 10:25:13.398106: Wireless event: new AP: 00:18:4d:4c:e0:6c
Sep 21 10:25:13.398132: State: ASSOCIATING -> ASSOCIATED
Sep 21 10:25:13.398191: Associated to a new BSS: BSSID=00:18:4d:4c:e0:6c
Sep 21 10:25:13.398225: No keys have been configured - skip key clearing
Sep 21 10:25:13.398247: Associated with 00:18:4d:4c:e0:6c
Sep 21 10:25:13.398287: WPA: Association event - clear replay counter
Sep 21 10:25:13.398316: Setting authentication timeout: 10 sec 0 usec
Sep 21 10:25:13.398353: RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
Sep 21 10:25:13.401878: RX EAPOL from 00:18:4d:4c:e0:6c
Sep 21 10:25:13.401946: RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 12 ff 9e 0d c1 b0 86 3b 15 e0 32 71 a7 53 03 c7 eb fb 0f 1e 11 32 75 22 9b a6 bb 8b 92 30 04 1f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 10:25:13.402016: Setting authentication timeout: 10 sec 0 usec
Sep 21 10:25:13.402049: IEEE 802.1X RX: version=1 type=3 length=95
Sep 21 10:25:13.402069:   EAPOL-Key type=254
Sep 21 10:25:13.402086:   key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
Sep 21 10:25:13.402105:   key_length=32 key_data_length=0
Sep 21 10:25:13.402120:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
Sep 21 10:25:13.402140:   key_nonce - hexdump(len=32): 12 ff 9e 0d c1 b0 86 3b 15 e0 32 71 a7 53 03 c7 eb fb 0f 1e 11 32 75 22 9b a6 bb 8b 92 30 04 1f
Sep 21 10:25:13.402171:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 10:25:13.402193:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
Sep 21 10:25:13.402221:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
Sep 21 10:25:13.402240:   key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 10:25:13.402262: WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 12 ff 9e 0d c1 b0 86 3b 15 e0 32 71 a7 53 03 c7 eb fb 0f 1e 11 32 75 22 9b a6 bb 8b 92 30 04 1f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 10:25:13.402352: State: ASSOCIATED -> 4WAY_HANDSHAKE
Sep 21 10:25:13.402370: WPA: RX message 1 of 4-Way Handshake from 00:18:4d:4c:e0:6c (ver=1)
Sep 21 10:25:13.402394: WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 10:25:13.403864: WPA: Renewed SNonce - hexdump(len=32): 15 3e e7 96 39 df 59 95 b7 7b cd ff 0a 98 2f 5d d8 a3 94 c5 f4 6e 3e eb 98 c7 e6 86 71 f0 3d c5
Sep 21 10:25:13.404015: WPA: PMK - hexdump(len=32): 33 f5 97 be 96 ef c4 b8 69 3f 9c 88 54 4c 00 30 93 7e 00 c1 3c c3 21 c6 f8 98 04 9d 91 76 d8 56
Sep 21 10:25:13.404052: WPA: PTK - hexdump(len=64): a2 e7 20 51 4d 65 81 75 02 76 23 0a 19 48 be 7b ca ad 63 48 1e 14 0b cc 1f 49 20 35 56 ac 1f 86 9a d1 c3 6c eb 7e 96 06 da 7b a9 3c 80 39 38 8a fd df c4 78 47 a4 53 a9 82 03 0b 4c 5c 18 9d 98
Sep 21 10:25:13.404092: WPA: Sending EAPOL-Key 2/4
Sep 21 10:25:13.404116: WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 15 3e e7 96 39 df 59 95 b7 7b cd ff 0a 98 2f 5d d8 a3 94 c5 f4 6e 3e eb 98 c7 e6 86 71 f0 3d c5 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 44 c5 c9 31 46 88 16 43 f3 2a ea 66 96 54 42 02 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 10:25:13.408520: RX EAPOL from 00:18:4d:4c:e0:6c
Sep 21 10:25:13.408552: RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 12 ff 9e 0d c1 b0 86 3b 15 e0 32 71 a7 53 03 c7 eb fb 0f 1e 11 32 75 22 9b a6 bb 8b 92 30 04 1f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 94 db e2 75 8f 83 bd 11 ac 15 f6 15 c3 2c 40 06 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 10:25:13.408619: IEEE 802.1X RX: version=1 type=3 length=119
Sep 21 10:25:13.408636:   EAPOL-Key type=254
Sep 21 10:25:13.408651:   key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
Sep 21 10:25:13.408669:   key_length=32 key_data_length=24
Sep 21 10:25:13.408686:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
Sep 21 10:25:13.408705:   key_nonce - hexdump(len=32): 12 ff 9e 0d c1 b0 86 3b 15 e0 32 71 a7 53 03 c7 eb fb 0f 1e 11 32 75 22 9b a6 bb 8b 92 30 04 1f
Sep 21 10:25:13.408733:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 10:25:13.408755:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
Sep 21 10:25:13.408774:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
Sep 21 10:25:13.408793:   key_mic - hexdump(len=16): 94 db e2 75 8f 83 bd 11 ac 15 f6 15 c3 2c 40 06
Sep 21 10:25:13.408815: WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 12 ff 9e 0d c1 b0 86 3b 15 e0 32 71 a7 53 03 c7 eb fb 0f 1e 11 32 75 22 9b a6 bb 8b 92 30 04 1f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 94 db e2 75 8f 83 bd 11 ac 15 f6 15 c3 2c 40 06 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 10:25:13.408885: State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
Sep 21 10:25:13.408902: WPA: RX message 3 of 4-Way Handshake from 00:18:4d:4c:e0:6c (ver=1)
Sep 21 10:25:13.408920: WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 10:25:13.408950: WPA: Sending EAPOL-Key 4/4
Sep 21 10:25:13.408969: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2f 0e 51 4c 00 29 ef ed 2e 75 63 f3 df 1c a0 13 00 00
Sep 21 10:25:13.409037: WPA: Installing PTK to the driver.
Sep 21 10:25:13.409073: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
Sep 21 10:25:13.409095: wpa_driver_madwifi_set_key: alg=TKIP key_idx=0 set_tx=1 seq_len=6 key_len=32
ioctl[unknown???]: No such device or address
Sep 21 10:25:13.415392: WPA: Failed to set PTK to the driver.
Sep 21 10:25:13.415559: State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
Sep 21 10:25:17.403964: Wireless event: cmd=0x8b15 len=20
Sep 21 10:25:17.404099: Wireless event: new AP: 00:00:00:00:00:00
Sep 21 10:25:17.404133: Setting scan request: 0 sec 100000 usec
Sep 21 10:25:17.404158: Added BSSID 00:18:4d:4c:e0:6c into blacklist
Sep 21 10:25:17.404179: State: GROUP_HANDSHAKE -> DISCONNECTED
Sep 21 10:25:17.404201: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 21 10:25:17.404223: wpa_driver_madwifi_del_key: keyidx=0
Sep 21 10:25:17.404253: wpa_driver_madwifi_del_key: keyidx=1
Sep 21 10:25:17.404273: wpa_driver_madwifi_del_key: keyidx=2
Sep 21 10:25:17.404292: wpa_driver_madwifi_del_key: keyidx=3
Sep 21 10:25:17.404310: wpa_driver_madwifi_del_key: keyidx=0

```

---

### Post by sharkcohen on 2006-09-21
Ok, I had played with iwpriv yesterday, so today I set mode back to 0 and my AP to auto.  I'm so close, but for some reason it's failing at GROUP_HANDSHAKE:

wpa_supplicant.conf:

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=2
fast_reauth=1

network={
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP

        ssid="SHARKNET"
        #psk="carcharodon"
        psk=33f597be96efc4b8693f9c88544c0030937e00c13cc321c6f898049d9176d856
}

```

```

root@sharkdesk:/usr/local/sbin# ./wpa_supplicant -dd -K -t -i ath0 -D madwifi -c /etc/wpa_supplicant.conf
Sep 21 14:06:13.033471: Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A'
Sep 21 14:06:13.033733: Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Sep 21 14:06:13.033758: Reading configuration file '/etc/wpa_supplicant.conf'
Sep 21 14:06:13.033825: ctrl_interface='/var/run/wpa_supplicant'
Sep 21 14:06:13.034639: ctrl_interface_group=0
Sep 21 14:06:13.034690: eapol_version=1
Sep 21 14:06:13.034709: ap_scan=2
Sep 21 14:06:13.034725: fast_reauth=1
Sep 21 14:06:13.034745: Line: 7 - start of a new network block
Sep 21 14:06:13.034766: proto: 0x1
Sep 21 14:06:13.034784: key_mgmt: 0x2
Sep 21 14:06:13.034803: pairwise: 0x8
Sep 21 14:06:13.034820: group: 0x8
Sep 21 14:06:13.034843: ssid - hexdump_ascii(len=8):
     53 48 41 52 4b 4e 45 54                           SHARKNET        
Sep 21 14:06:13.034882: PSK - hexdump(len=32): 33 f5 97 be 96 ef c4 b8 69 3f 9c 88 54 4c 00 30 93 7e 00 c1 3c c3 21 c6 f8 98 04 9d 91 76 d8 56
Sep 21 14:06:13.034930: Priority group 0
Sep 21 14:06:13.034954:    id=0 ssid='SHARKNET'
Sep 21 14:06:13.034974: Initializing interface (2) 'ath0'
Sep 21 14:06:13.035117: SIOCGIWRANGE: WE(compiled)=19 WE(source)=13 enc_capa=0xf
Sep 21 14:06:13.035145:   capabilities: key_mgmt 0xf enc 0xf
Sep 21 14:06:13.057618: Own MAC address: 00:14:6c:89:40:a9
Sep 21 14:06:13.057660: wpa_driver_madwifi_del_key: keyidx=0
Sep 21 14:06:13.057707: wpa_driver_madwifi_del_key: keyidx=1
Sep 21 14:06:13.057728: wpa_driver_madwifi_del_key: keyidx=2
Sep 21 14:06:13.057747: wpa_driver_madwifi_del_key: keyidx=3
Sep 21 14:06:13.057767: wpa_driver_madwifi_set_countermeasures: enabled=0
Sep 21 14:06:13.057804: wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Sep 21 14:06:13.057841: Setting scan request: 0 sec 100000 usec
Sep 21 14:06:13.057881: Using existing control interface directory.
bind(PF_UNIX): Address already in use
Sep 21 14:06:13.058028: ctrl_iface exists, but does not allow connections - assuming it was leftover from forced program termination
Sep 21 14:06:13.058074: Successfully replaced leftover ctrl_iface socket '/var/run/wpa_supplicant/ath0'
Sep 21 14:06:13.058107: Added interface ath0
Sep 21 14:06:13.058175: Wireless event: cmd=0x8b06 len=8
Sep 21 14:06:13.161627: State: DISCONNECTED -> SCANNING
Sep 21 14:06:13.161674: Trying to associate with SSID 'SHARKNET'
Sep 21 14:06:13.161697: Cancelling scan request
Sep 21 14:06:13.161713: WPA: clearing own WPA/RSN IE
Sep 21 14:06:13.161732: Automatic auth_alg selection: 0x1
Sep 21 14:06:13.161759: WPA: No WPA/RSN IE available from association info
Sep 21 14:06:13.161778: WPA: Set cipher suites based on configuration
Sep 21 14:06:13.161794: WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
Sep 21 14:06:13.161812: WPA: clearing AP WPA IE
Sep 21 14:06:13.161827: WPA: clearing AP RSN IE
Sep 21 14:06:13.161843: WPA: using GTK TKIP
Sep 21 14:06:13.161859: WPA: using PTK TKIP
Sep 21 14:06:13.161876: WPA: using KEY_MGMT WPA-PSK
Sep 21 14:06:13.161893: WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 14:06:13.161922: No keys have been configured - skip key clearing
Sep 21 14:06:13.161939: wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Sep 21 14:06:13.161957: State: SCANNING -> ASSOCIATING
Sep 21 14:06:13.161974: wpa_driver_madwifi_associate
Sep 21 14:06:13.162014: Setting authentication timeout: 60 sec 0 usec
Sep 21 14:06:13.162056: Wireless event: cmd=0x8b1a len=17
Sep 21 14:06:14.269863: Wireless event: cmd=0x8b19 len=8
Sep 21 14:06:14.270588: Scan results did not fit - trying larger buffer (8192 bytes)
Sep 21 14:06:14.271434: Received 4419 bytes of scan results (22 BSSes)
Sep 21 14:06:14.271848: Scan results: 22
Sep 21 14:06:14.274447: Wireless event: cmd=0x8b15 len=20
Sep 21 14:06:14.274500: Wireless event: new AP: 00:18:4d:4c:e0:6c
Sep 21 14:06:14.274524: State: ASSOCIATING -> ASSOCIATED
Sep 21 14:06:14.274560: Associated to a new BSS: BSSID=00:18:4d:4c:e0:6c
Sep 21 14:06:14.274581: No keys have been configured - skip key clearing
Sep 21 14:06:14.274604: Network configuration found for the current AP
Sep 21 14:06:14.274640: WPA: Using WPA IE from AssocReq to set cipher suites
Sep 21 14:06:14.274658: WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2
Sep 21 14:06:14.274676: WPA: clearing AP WPA IE
Sep 21 14:06:14.274692: WPA: clearing AP RSN IE
Sep 21 14:06:14.274708: WPA: using GTK TKIP
Sep 21 14:06:14.274726: WPA: using PTK TKIP
Sep 21 14:06:14.274743: WPA: using KEY_MGMT WPA-PSK
Sep 21 14:06:14.274760: WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 14:06:14.274792: Associated with 00:18:4d:4c:e0:6c
Sep 21 14:06:14.274809: WPA: Association event - clear replay counter
Sep 21 14:06:14.274828: Setting authentication timeout: 10 sec 0 usec
Sep 21 14:06:14.274864: RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
Sep 21 14:06:14.280211: RX EAPOL from 00:18:4d:4c:e0:6c
Sep 21 14:06:14.280557: RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 1d d8 f7 67 bf 6a 28 35 05 05 8f 85 83 fa 9e 4a 21 5b e0 2e 71 ee 2d 6b be 76 e4 6d d6 dd e0 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 14:06:14.281026: Setting authentication timeout: 10 sec 0 usec
Sep 21 14:06:14.281218: IEEE 802.1X RX: version=1 type=3 length=95
Sep 21 14:06:14.281409:   EAPOL-Key type=254
Sep 21 14:06:14.281581:   key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
Sep 21 14:06:14.281884:   key_length=32 key_data_length=0
Sep 21 14:06:14.281919:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
Sep 21 14:06:14.281942:   key_nonce - hexdump(len=32): 1d d8 f7 67 bf 6a 28 35 05 05 8f 85 83 fa 9e 4a 21 5b e0 2e 71 ee 2d 6b be 76 e4 6d d6 dd e0 3c
Sep 21 14:06:14.281971:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 14:06:14.281993:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
Sep 21 14:06:14.282038:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
Sep 21 14:06:14.282059:   key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 14:06:14.282081: WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 01 1d d8 f7 67 bf 6a 28 35 05 05 8f 85 83 fa 9e 4a 21 5b e0 2e 71 ee 2d 6b be 76 e4 6d d6 dd e0 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 14:06:14.282250: State: ASSOCIATED -> 4WAY_HANDSHAKE
Sep 21 14:06:14.282269: WPA: RX message 1 of 4-Way Handshake from 00:18:4d:4c:e0:6c (ver=1)
Sep 21 14:06:14.282296: WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 14:06:14.283778: WPA: Renewed SNonce - hexdump(len=32): 1d 76 0b 87 b1 4d ab 6e 20 96 62 1c 73 3b 6d d1 fe 66 d1 41 2e f2 30 a1 cf f3 fd 38 e3 73 83 26
Sep 21 14:06:14.283872: WPA: PMK - hexdump(len=32): 33 f5 97 be 96 ef c4 b8 69 3f 9c 88 54 4c 00 30 93 7e 00 c1 3c c3 21 c6 f8 98 04 9d 91 76 d8 56
Sep 21 14:06:14.283906: WPA: PTK - hexdump(len=64): 75 e0 80 85 ff f4 a9 1a c7 6f a2 a2 fb 8d 27 95 eb 0d 61 44 a9 84 a4 9b 49 05 a0 1a eb c5 f3 92 a1 40 44 94 cb 13 46 1b 44 09 96 66 d8 5c ed 0a 54 a6 5e 45 ac cb e9 60 d8 17 59 86 75 f6 b8 c8
Sep 21 14:06:14.283946: WPA: Sending EAPOL-Key 2/4
Sep 21 14:06:14.283972: WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 01 1d 76 0b 87 b1 4d ab 6e 20 96 62 1c 73 3b 6d d1 fe 66 d1 41 2e f2 30 a1 cf f3 fd 38 e3 73 83 26 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 d1 47 bf b9 84 0a af c0 9b 7b 9e 84 04 ec 74 4d 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 14:06:14.288188: RX EAPOL from 00:18:4d:4c:e0:6c
Sep 21 14:06:14.288225: RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 1d d8 f7 67 bf 6a 28 35 05 05 8f 85 83 fa 9e 4a 21 5b e0 2e 71 ee 2d 6b be 76 e4 6d d6 dd e0 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ce ad a1 0f 61 a8 57 d7 d5 0c 31 22 fe b2 09 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 14:06:14.288325: IEEE 802.1X RX: version=1 type=3 length=119
Sep 21 14:06:14.288344:   EAPOL-Key type=254
Sep 21 14:06:14.288364:   key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
Sep 21 14:06:14.288381:   key_length=32 key_data_length=24
Sep 21 14:06:14.288397:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
Sep 21 14:06:14.288415:   key_nonce - hexdump(len=32): 1d d8 f7 67 bf 6a 28 35 05 05 8f 85 83 fa 9e 4a 21 5b e0 2e 71 ee 2d 6b be 76 e4 6d d6 dd e0 3c
Sep 21 14:06:14.288442:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Sep 21 14:06:14.288464:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
Sep 21 14:06:14.288482:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
Sep 21 14:06:14.288501:   key_mic - hexdump(len=16): 00 ce ad a1 0f 61 a8 57 d7 d5 0c 31 22 fe b2 09
Sep 21 14:06:14.288522: WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 c9 00 20 00 00 00 00 00 00 00 02 1d d8 f7 67 bf 6a 28 35 05 05 8f 85 83 fa 9e 4a  21 5b e0 2e 71 ee 2d 6b be 76 e4 6d d6 dd e0 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ce ad a1 0f 61 a8 57 d7 d5 0c 31 22 fe b2 09 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 14:06:14.288594: State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
Sep 21 14:06:14.288642: WPA: RX message 3 of 4-Way Handshake from 00:18:4d:4c:e0:6c (ver=1)
Sep 21 14:06:14.288661: WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 14:06:14.288689: WPA: No WPA/RSN IE for this AP known. Trying to get from scan results
Sep 21 14:06:14.288705: WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
Sep 21 14:06:14.288741: WPA: clearing AP RSN IE
Sep 21 14:06:14.288757: WPA: Found the current AP from updated scan results
Sep 21 14:06:14.288775: WPA: Sending EAPOL-Key 4/4
Sep 21 14:06:14.288792: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b2 91 08 49 b2 21 3f 91 95 4b 50 11 64 7f 19 54 00 00
Sep 21 14:06:14.288864: WPA: Installing PTK to the driver.
Sep 21 14:06:14.288908: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
Sep 21 14:06:14.288929: wpa_driver_madwifi_set_key: alg=TKIP key_idx=0 set_tx=1 seq_len=6 key_len=32
Sep 21 14:06:14.288970: State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
Sep 21 14:06:15.439865: Wireless event: cmd=0x8b15 len=20
Sep 21 14:06:15.440007: Wireless event: new AP: 00:00:00:00:00:00
Sep 21 14:06:15.440065: Setting scan request: 0 sec 100000 usec
Sep 21 14:06:15.440090: Added BSSID 00:18:4d:4c:e0:6c into blacklist
Sep 21 14:06:15.440111: State: GROUP_HANDSHAKE -> DISCONNECTED
Sep 21 14:06:15.440128: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Sep 21 14:06:15.440146: wpa_driver_madwifi_del_key: keyidx=0
Sep 21 14:06:15.440180: wpa_driver_madwifi_del_key: keyidx=1
Sep 21 14:06:15.440200: wpa_driver_madwifi_del_key: keyidx=2
Sep 21 14:06:15.440219: wpa_driver_madwifi_del_key: keyidx=3
Sep 21 14:06:15.440238: wpa_driver_madwifi_del_key: keyidx=0
Sep 21 14:06:15.440278: RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
Sep 21 14:06:15.541859: State: DISCONNECTED -> SCANNING
Sep 21 14:06:15.541922: Trying to associate with SSID 'SHARKNET'

```

:-k

---

### Post by sharkcohen on 2006-09-22
If I need to provide anymore information, please let me know.  I'm currently running 128 bit WEP, and that is unacceptable to me.

---

### Post by tturrisi on 2006-09-22
[http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends](http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends)

---

### Post by sharkcohen on 2006-09-22
> **tturrisi said:**
> [http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends](http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends)

I've been through that.  I'm looking for assistance as to why it's not working, which is why I posted my wpa_supplicant output.

---

### Post by sharkcohen on 2006-09-24
Ok, I've been through the pages on madwifi.org, the README for wpa_supplicant, the Wiki here, and several threads here in the forum, and have gotten nowhere with this.  Still get up to the Group Handshake and then everything disconnects.  knetworkmanager has been useless.  WEP is working fine, so I know my wireless is working.

Is everyone just tired of addressing wpa issues?  I'm surprised at the lack of response to this thread.  Please let me know if I should be posting more info, I can post whatever you guys need.

---

### Post by sharkcohen on 2006-09-27
Ok, I was able to get this working.  I don't fully understand why what I originally tried did not work, nor why I had to configure it as I have.  It seems my original configuration should have worked for WPA1 (which is what I was shooting for).  I came across information which led me to attempt WPA2, which is now working great, and is more secure anyway.  What I can do is post my hardware and configs so that it might help others in the future.

access point: Netgear WGT624
mode: G only
encryption:  WPA-PSK [TKIP] + WPA2-PSK [AES]
ssid broadcast enabled (haven't tried it disabled yet)

card: Netgear WG311T (PCI card)
latest madwifi-ng from CVS
wpa_supplicant-0.4.9

```

root@sharkdesk:/home/sharkcohen# uname -a
Linux sharkdesk 2.6.15-26-686 #1 SMP PREEMPT Fri Sep 8 20:16:40 UTC 2006 i686 GNU/Linux

root@sharkdesk:/home/sharkcohen# cat /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=2
ap_scan=1
fast_reauth=1

network={
        ssid="SHARKNET"
        scan_ssid=0
        #bssid=00:18:4D:4C:E0:6C
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP WEP104 WEP40
        #psk="***********"
        psk=****************************************************************
        #priority=1
}

root@sharkdesk:/home/sharkcohen# cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
pre-up  /usr/local/sbin/wpa_supplicant -B -D madwifi -i ath0 -c /etc/wpa_supplicant.conf
#pre-up modprobe ath_pci xchanmode=0
#pre-up iwconfig ath0 essid "SHARKNET"
#pre-up iwconfig ath0 ap 00:18:4D:4C:E0:6C
#pre-up iwconfig ath0 key 1A82C4CB04AA8B56FC19A0668B
#pre-up iwconfig ath0 channel 2
#pre-up iwpriv ath0 mode 3
#pre-up iwpriv ath0 authmode 2

#auto wlan0
#iface wlan0 inet dhcp

```

I decided on trying WPA2 (proto=RSN) when I noticed this entry in the userdocs section on the madwifi site:

[http://www.translever.com/howto/wifi/madwifi-wpa_supplicant_RSN_howto/madwifi-wpa_supplicant_RSN_howto.html](http://www.translever.com/howto/wifi/madwifi-wpa_supplicant_RSN_howto/madwifi-wpa_supplicant_RSN_howto.html)

Although the title refers to RSN, I noticed it was referencing an error I was seeing when trying to use the madwifi driver rather than wext with WPA1, i.e. ioctl[unknown???]: Invalid argument.  So I decided to attempt the RSN setup.  It didn't seem to start working for me until I changed eapol_version from 1 to 2.  I haven't troubleshooted things further to figure out exactly what particular setting(s) did the trick.  I may do that in the future, and if I do I will provide the additional information here.

---

### Post by wieman01 on 2006-09-27
Hey SharkCohen, Bollocks00 has got wireless working (no security). So we could use your experience with WPA(2) as well. :-)

[http://www.ubuntuforums.org/showthread.php?t=265512&page=4]("http://www.ubuntuforums.org/showthread.php?t=265512&page=4")

Let's try tomorrow.

---

### Post by sharkcohen on 2006-09-27
Definitely, I'll be keeping an eye on the thread.

---

