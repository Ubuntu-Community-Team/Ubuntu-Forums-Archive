---
title: "Inprocomm IPN 2220 &amp; WPA issue"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by MacGeneral on 2008-01-17
I searched google and this forums for days now and tried several tutorials but I don't get WPA to work.

My internal wireless chip works without any problems on unsecured or WEP protected networks (if I use the default linux wireless-tools to configure (ifconfig, iwconfig etc))... but we all know that WEP is unsecure and even a MAC filter doesn't help because MAC addresses can be spoofed easily.
So I want to switch (back) to WPA-PSK (and maybe WPA2-AES if I would get WPA1 to work), but I tried everything and failed.

Notebook: Acer Aspire 1520
Processor: AMD Athlon 64 3200+
System: Debian Lenny/Sid (unstable/testing)
Kernel: 2.6.23-1-amd64
Gnome: 2.20.3

my wireless card
```
lspci | grep IPN
00:0a.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
```

I use the WinXP 64 Bit driver along with ndiswrapper (from [Acer Europe]("http://support.acer-euro.com/drivers/notebook/as_1520.html"))

```
sudo ndiswrapper -l
neti2220 : driver installed
	device (17FE:2220) present

```


but when I try wpa_supplicant it tries to connect in an endless-loop (the text at the end of this post is repeated until I kill wpa_supplicant with CTRL + C):
(it doesn't make a difference  if I use -Dndiswrapper (I know this was for older versions of wpa_supplicant/ndiswrapper only) or -Dwext)

I also cut down my config file to a minimum (I had all types of config files but none worked):
```
# allow frontend (e.g., wpa_cli) to be used by all users in 'wheel' group
ctrl_interface=/var/run/wpa_supplicant
#ctrl_interface_group=wheel

ap_scan=0 # 1 or 2 don't make a difference either!
#
# home network; allow all valid ciphers
network={
	ssid="NFG"
	proto=WPA
	key_mgmt=WPA-PSK
	psk="super secret key"
	# pairwise=TKIP
	# group=TKIP CCMP
}
```

The router is set up to use WPA-PSK along with TKIP and no difference if it broadcasts its SSID or not.


Note: if I start up wpa_gui it always says "Could not get status from wpa_supplicant"

Note 2: I compiled different versions (stable and unstable) of wpa_supplicant myself and used the packages precompiled by the Debian team... no difference


Thanks for your help (if anyone can ;))



here is the output of wpa_supplicant:

> macgeneral@Acer-Aspire1520:/etc/network$ sudo wpa_supplicant -iwlan0 -Dndiswrapper -c/etc/wpa_supplicant.conf -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=0
Priority group 0
   id=0 ssid='NFG'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0e:9b:6f:77:68
Driver does not support WPA.
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b06 len=12
EAPOL: External notification - portControl=Auto
Already associated with a configured network - generating associated event
Association info event
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:0e:2e:a1:c6:96
No keys have been configured - skip key clearing
Network configuration found for the current AP
WPA: No WPA/RSN IE available from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 30 pairwise 24 key_mgmt 2 proto 1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Associated with 00:0e:2e:a1:c6:96
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
EAPOL: disable timer tick
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:0e:2e:a1:c6:96 into blacklist
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
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:00:00:00:00:00 into blacklist
No keys have been configured - skip key clearing
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=19
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=61
AssocReq IE wireless event - hexdump(len=45): 00 03 4e 46 47 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=32
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=24
Wireless event: new AP: 00:0e:2e:a1:c6:96
Association info event
req_ies - hexdump(len=45): 00 03 4e 46 47 01 08 02 04 0b 16 0c 12 18 24 32 04 30 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: DISCONNECTED -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:0e:2e:a1:c6:96
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
Associated with 00:0e:2e:a1:c6:96
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:0e:2e:a1:c6:96
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 0a 84
  key_nonce - hexdump(len=32): 34 f6 53 7f 36 c1 97 ed b2 00 7b cf ab 48 2f a9 c6 51 47 0e 5b 62 99 20 4f da 94 5d e8 1a 77 95
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:0e:2e:a1:c6:96 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): 3c 1f c4 b6 71 20 91 28 6d c6 e5 33 14 14 fd cc d1 61 b0 a7 52 9f 46 05 60 48 ea 83 f8 4b 8f c0
WPA: PTK derivation - A1=00:0e:9b:6f:77:68 A2=00:0e:2e:a1:c6:96
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:0e:2e:a1:c6:96
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 0a 85
  key_nonce - hexdump(len=32): 34 f6 53 7f 36 c1 97 ed b2 00 7b cf ab 48 2f a9 c6 51 47 0e 5b 62 99 20 4f da 94 5d e8 1a 77 95
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 6a ac eb 2e 8f 2f e1 ab 9f c0 30 87 d5 de a9 b7
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:0e:2e:a1:c6:96 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: No WPA/RSN IE for this AP known. Trying to get from scan results
Received 1326 bytes of scan results (4 BSSes)
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: Found the current AP from updated scan results
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
WPA: Failed to set PTK to the driver.
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: GROUP_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
Failed to disable WPA in the driver.
No keys have been configured - skip key clearing
Removed BSSID 00:00:00:00:00:00 from blacklist (clear)
Removed BSSID 00:0e:2e:a1:c6:96 from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6


edit: in the output of wpa_supplicant it says (line 20):
> Driver does not support WPA.

but when ndiswrapper startsup it shows:
> ndiswrapper: using IRQ 21
wlan0: ethernet device 00:0e:9b:6f:77:68 using NDIS driver: neti2220, version: 0x30007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 17FE:2220.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


---

