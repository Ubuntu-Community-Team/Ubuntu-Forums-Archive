---
title: "WPA causing mass syslog entries in Fiesty"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by alighieri on 2007-12-22
WPA is working fine with Restricted drivers installed for Intel Pro 3945 connecting to a Asus router.

The problem i have found is that the syslog is constantly being filled with the following every few seconds.


Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): IEEE 802.1X RX: version=1 type=3 length=119 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):   EAPOL-Key type=254 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):   key_info 0x392 (ver=2 keyidx=1 rsvd=0 Group Ack MIC Secure) 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):   key_length=16 key_data_length=24 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):   replay_counter - hexdump(len=8): 00 00 00 00 00 01 a4 b3 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):   key_nonce - hexdump(len=32): 5a 7d ce 79 32 db 2d 1d e0 67 32 4b f5 6e da 00 b6
 a6 75 fc 4f f3 98 49 74 30 0b 12 98 43 af cb 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):   key_iv - hexdump(len=16): b6 a6 75 fc 4f f3 98 49 74 30 0b 12 98 43 af cc 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):   key_mic - hexdump(len=16): b6 82 f6 e9 08 ab f6 37 4d 54 6f 21 43 ff cc 2a 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): xxxx
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): WPA: RX message 1 of Group Key or STAKey Handshake from 00:11:d8:1b:fa:f3 (ver=2)
 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): State: COMPLETED -> GROUP_HANDSHAKE 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): WPA: Group Key - hexdump(len=16): [REMOVED] 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): WPA: Installing GTK to the driver (keyidx=1 tx=0). 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): WPA: RSC - hexdump(len=6): 00 00 00 00 00 00 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): WPA: Sending EAPOL-Key 2/2 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): WPA: TX EAPOL-Key - hexdump(len=99): xxxx
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): WPA: Group rekeying completed with 00:11:d8:1b:fa:f3 [GTK=CCMP] 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035):  72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 32 30 38 2d 32 00 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): State: GROUP_HANDSHAKE -> COMPLETED 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): RX EAPOL from 00:11:d8:1b:fa:f3 
Dec 23 01:23:53 Munkeh NetworkManager: <information>^Iwpa_supplicant(6035): RX EAPOL - hexdump(len=123): xxxx


(xxxx = removed hex dump values)

Anyone have an idea as to what is causing this?

---

