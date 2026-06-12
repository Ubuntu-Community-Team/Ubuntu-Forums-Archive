---
title: "wpa_psk not working with edgy eft"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by viveknz76 on 2006-11-04
Hi,

I have tried the steps mentioned in the threads to configure the wpa but I am getting an error. Initially when I start my laptop that has ipw2200 shows activity of sending and receiving but once I execute the following
> 
sudo wpa_supplicant -w -D wext -i eth1 -c /etc/wpa_supplicant.conf -dd

the icon in the tray shows disconnected and throws the following error.  Please help.

> Wireless event: new AP: 00:00:00:00:00:00
BSSID 00:00:00:00:00:00 blacklist count incremented to 4
State: ASSOCIATING -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
Wireless event: cmd=0x8b19 len=8
Received 1156 bytes of scan results (5 BSSes)
Scan results: 5
Wireless event: cmd=0x8b19 len=8
Received 1153 bytes of scan results (5 BSSes)
Scan results: 5
Wireless event: cmd=0x8b19 len=8
Received 1155 bytes of scan results (5 BSSes)
Scan results: 5
Wireless event: cmd=0x8b19 len=8
Received 1153 bytes of scan results (5 BSSes)
Scan results: 5


---

