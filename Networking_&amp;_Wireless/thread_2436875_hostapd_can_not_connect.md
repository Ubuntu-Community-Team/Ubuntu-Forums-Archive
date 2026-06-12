---
title: "hostapd: can not connect"
date: 2020-02-14
forum: Networking &amp; Wireless
---

### Post by mcaddress on 2020-02-14
Hello,

I'm trying to set up a WLAN access point using hostapd. Unfortunately, I was not able to connect to it yet and I don't know what I'm doing wrong.
Hardware is a Raspberry Pi 4, operating system is Ubuntu Server 19.10.1 arm64 raspi3, hostapd v2.9.

hostapd.conf:
```
interface=wlan0
ssid=MySSID
country_code=DE
ieee80211d=1
ieee80211h=1
hw_mode=g
channel=10
auth_algs=1
wmm_enabled=1
ieee80211n=1
wpa=2
wpa_passphrase=Secret
wpa_key_mgmt=WPA-PSK
rsn_pairwise=TKIP CCMP
driver=nl80211
```

When I start hostapd (sudo hostapd -dd /etc/hostapd/hostapd.conf), I can see the wlan MySSID on other devices. When I try to connect to it with a Windows 10 tablet, I get the message "connection not possible" from Windows. hostapd does not print any message, the output does not change. When I try to connect with my Android mobile phone, I get the message "Authentication failed" though I double checked the password. In the output of hostapd there are 4 "New STA" messages. To be sure, I also entered a wrong password on purpose and then the behaviour was different. On my phone I got the message "Wrong password" and also the output of hostapd was different with only one "new STA" message (the last one). I don't know what else I can try and what I'm doing wrong.

Any help is appreciated.


Output of hostapd:
```
random: getrandom() support available
Configuration file: /etc/hostapd/hostapd.conf
nl80211: Using driver-based roaming
nl80211: TDLS supported
nl80211: Supported cipher 00-0f-ac:1
nl80211: Supported cipher 00-0f-ac:5
nl80211: Supported cipher 00-0f-ac:2
nl80211: Supported cipher 00-0f-ac:4
nl80211: Supported cipher 00-0f-ac:6
nl80211: Using driver-based off-channel TX
nl80211: Supported vendor command: vendor_id=0x1018 subcmd=1
nl80211: Use separate P2P group interface (driver advertised support)
nl80211: Enable multi-channel concurrent (driver advertised support)
nl80211: use P2P_DEVICE support
nl80211: interface wlan0 in phy phy0
nl80211: Set mode ifindex 4 iftype 3 (AP)
nl80211: Setup AP(wlan0) - device_ap_sme=1 use_monitor=0
nl80211: Subscribe to mgmt frames with AP handle 0xaaab164a5720 (device SME)
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=04
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=0501
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=0503
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=0504
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=06
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=08
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=09
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=0a
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=11
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=12
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0xaaab164a5720 match=7f
nl80211: Register frame type=0xb0 (WLAN_FC_STYPE_AUTH) nl_handle=0xaaab164a5720 match=
nl80211: Enable Probe Request reporting nl_preq=0xaaab164aa160
nl80211: Register frame type=0x40 (WLAN_FC_STYPE_PROBE_REQ) nl_handle=0xaaab164aa160 match=
rfkill: initial event: idx=0 type=1 op=0 soft=0 hard=0
nl80211: Add own interface ifindex 4 (ifidx_reason -1)
nl80211: if_indices[16]: 4(-1)
phy: phy0
BSS count 1, BSSID mask 00:00:00:00:00:00 (0 bits)
wlan0: interface state UNINITIALIZED->COUNTRY_UPDATE
Previous country code 00, new country code DE 
Continue interface setup after channel list update
ctrl_iface not configured!
Channel list update timeout - try to continue anyway
nl80211: Regulatory information - country=00
nl80211: 2402-2472 @ 40 MHz 20 mBm
nl80211: 2457-2482 @ 20 MHz 20 mBm (no IR)
nl80211: 2474-2494 @ 20 MHz 20 mBm (no OFDM) (no IR)
nl80211: 5170-5250 @ 80 MHz 20 mBm (no IR)
nl80211: 5250-5330 @ 80 MHz 20 mBm (DFS) (no IR)
nl80211: 5490-5730 @ 160 MHz 20 mBm (DFS) (no IR)
nl80211: 5735-5835 @ 80 MHz 20 mBm (no IR)
nl80211: 57240-63720 @ 2160 MHz 0 mBm
nl80211: Added 802.11b mode based on 802.11g information
nl80211: Mode IEEE 802.11g: 2412 2417 2422 2427 2432 2437 2442 2447 2452 2457 2462 2467 2472 2484
nl80211: Mode IEEE 802.11a: 5170 5180 5190 5200 5210 5220 5230 5240 5260 5280 5300 5320 5500 5520 5540 5560 5580 5600 5620 5640 5660 5680 5700 5720 5745 5765 5785 5805 5825
nl80211: Mode IEEE 802.11b: 2412 2417 2422 2427 2432 2437 2442 2447 2452 2457 2462 2467 2472 2484
Allowed channel: mode=1 chan=1 freq=2412 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=2 freq=2417 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=3 freq=2422 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=4 freq=2427 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=5 freq=2432 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=6 freq=2437 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=7 freq=2442 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=8 freq=2447 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=9 freq=2452 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=10 freq=2457 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=11 freq=2462 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=12 freq=2467 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=13 freq=2472 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=14 freq=2484 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=34 freq=5170 MHz max_tx_power=3 dBm
Allowed channel: mode=2 chan=36 freq=5180 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=38 freq=5190 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=40 freq=5200 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=42 freq=5210 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=44 freq=5220 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=46 freq=5230 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=48 freq=5240 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=52 freq=5260 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=56 freq=5280 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=60 freq=5300 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=64 freq=5320 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=100 freq=5500 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=104 freq=5520 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=108 freq=5540 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=112 freq=5560 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=116 freq=5580 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=120 freq=5600 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=124 freq=5620 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=128 freq=5640 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=132 freq=5660 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=136 freq=5680 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=140 freq=5700 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=144 freq=5720 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=149 freq=5745 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=153 freq=5765 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=157 freq=5785 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=161 freq=5805 MHz max_tx_power=20 dBm
Allowed channel: mode=2 chan=165 freq=5825 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=1 freq=2412 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=2 freq=2417 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=3 freq=2422 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=4 freq=2427 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=5 freq=2432 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=6 freq=2437 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=7 freq=2442 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=8 freq=2447 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=9 freq=2452 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=10 freq=2457 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=11 freq=2462 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=12 freq=2467 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=13 freq=2472 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=14 freq=2484 MHz max_tx_power=20 dBm
DFS support is enabled
Completing interface initialization
Mode: IEEE 802.11g  Channel: 10  Frequency: 2457 MHz
DFS 0 channels required radar detection
nl80211: Set freq 2457 (ht_enabled=1, vht_enabled=0, he_enabled=0, bandwidth=20 MHz, cf1=2457 MHz, cf2=0 MHz)
  * freq=2457
  * he_enabled=0
  * vht_enabled=0
  * ht_enabled=1
  * sec_channel_offset=0
  * channel_type=1
RATE[0] rate=10 flags=0x1
RATE[1] rate=20 flags=0x1
RATE[2] rate=55 flags=0x1
RATE[3] rate=110 flags=0x1
RATE[4] rate=60 flags=0x0
RATE[5] rate=90 flags=0x0
RATE[6] rate=120 flags=0x0
RATE[7] rate=180 flags=0x0
RATE[8] rate=240 flags=0x0
RATE[9] rate=360 flags=0x0
RATE[10] rate=480 flags=0x0
RATE[11] rate=540 flags=0x0
hostapd_setup_bss(hapd=0xaaab164a3c00 (wlan0), first=1)
wlan0: Flushing old station entries
nl80211: flush -> DEL_STATION wlan0 (all)
nl80211: Station flush failed: ret=-14 (Bad address)
wlan0: Could not connect to kernel driver
wlan0: Deauthenticate all stations
nl80211: sta_remove -> DEL_STATION wlan0 ff:ff:ff:ff:ff:ff --> 0 (Success)
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=0 set_tx=0 seq_len=0 key_len=0
nl80211: set_key failed; err=-22 Invalid argument)
Failed to clear default encryption keys (ifname=wlan0 keyidx=0)
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=3 set_tx=0 seq_len=0 key_len=0
nl80211: set_key failed; err=-22 Invalid argument)
Failed to clear default encryption keys (ifname=wlan0 keyidx=3)
Using interface wlan0 with hwaddr aa:bb:cc:dd:ee:ff and ssid "MySSID"
Deriving WPA PSK based on passphrase
SSID - hexdump_ascii(len=6):
     4d 79 53 53 49 44                                 MySSID          
PSK (ASCII passphrase) - hexdump_ascii(len=17): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
random: Got 20/20 random bytes
Get randomness: len=32 entropy=0
GMK - hexdump(len=32): [REMOVED]
Get randomness: len=32 entropy=0
Key Counter - hexdump(len=32): [REMOVED]
WPA: Delay group state machine start until Beacon frames have been configured
nl80211: Set beacon (beacon_set=0)
nl80211: Beacon head - hexdump(len=57): 80 00 00 00 ff ff ff ff ff ff dc a6 32 51 66 21 dc a6 32 51 66 21 00 00 00 00 00 00 00 00 00 00 64 00 11 04 00 06 4d 79 53 53 49 44 01 08 82 84 8b 96 0c 12 18 24 03 01 0a
nl80211: Beacon tail - hexdump(len=127): 07 06 44 45 20 01 0e 14 2a 01 04 32 04 30 48 60 6c 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 0c 00 2d 1a 0c 00 1f ff 00 00 00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 3d 16 0a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7f 04 00 00 00 02 dd 18 00 50 f2 02 01 01 01 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00
nl80211: ifindex=4
nl80211: beacon_int=100
nl80211: beacon_rate=0
nl80211: rate_type=0
nl80211: dtim_period=2
nl80211: ssid=MySSID
  * beacon_int=100
  * dtim_period=2
nl80211: hidden SSID not in use
nl80211: privacy=1
nl80211: auth_algs=0x1
nl80211: wpa_version=0x2
nl80211: key_mgmt_suites=0x2
nl80211: pairwise_ciphers=0x18
nl80211: group_cipher=0x8
nl80211: SMPS mode - off
nl80211: beacon_ies - hexdump(len=6): 7f 04 00 00 00 02
nl80211: proberesp_ies - hexdump(len=6): 7f 04 00 00 00 02
nl80211: assocresp_ies - hexdump(len=6): 7f 04 00 00 00 02
WPA: Start group state machine to set initial keys
WPA: group state machine entering state GTK_INIT (VLAN-ID 0)
Get randomness: len=32 entropy=0
GTK - hexdump(len=32): [REMOVED]
WPA: group state machine entering state SETKEYSDONE (VLAN-ID 0)
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=2 addr=0xaaaae74752b0 key_idx=1 set_tx=1 seq_len=0 key_len=32
nl80211: KEY_DATA - hexdump(len=32): [REMOVED]
   broadcast key
nl80211: Set wlan0 operstate 0->1 (UP)
netlink: Operstate: ifindex=4 linkmode=-1 (no change), operstate=6 (IF_OPER_UP)
nl80211: TX queue param set: queue=0 aifs=1 cw_min=3 cw_max=7 burst_time=15 --> res=-95
Failed to set TX queue parameters for queue 0.
nl80211: TX queue param set: queue=1 aifs=1 cw_min=7 cw_max=15 burst_time=30 --> res=-95
Failed to set TX queue parameters for queue 1.
nl80211: TX queue param set: queue=2 aifs=3 cw_min=15 cw_max=63 burst_time=0 --> res=-95
Failed to set TX queue parameters for queue 2.
nl80211: TX queue param set: queue=3 aifs=7 cw_min=15 cw_max=1023 burst_time=0 --> res=-95
Failed to set TX queue parameters for queue 3.
wlan0: interface state COUNTRY_UPDATE->ENABLED
wlan0: AP-ENABLED 
wlan0: Setup of interface done.
RTM_NEWLINK: ifi_index=4 ifname=wlan0 operstate=6 linkmode=0 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
VLAN: vlan_newlink(wlan0)
nl80211: Event message available
nl80211: Drv Event 19 (NL80211_CMD_NEW_STATION) received for wlan0
nl80211: New station XX:XX:XX:XX:XX:XX
nl80211: Assoc Req IEs - hexdump(len=175): 00 06 4d 79 53 53 49 44 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 21 02 03 14 24 02 01 0d 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00 2d 1a ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7f 08 00 00 08 00 00 00 00 40 dd 1e 00 90 4c 33 ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 dd 09 00 10 18 02 00 00 10 00 00 dd 07 00 50 f2 02 00 01 00 dd 1d 00 90 4c 5c 02 01 0a 00 08 07 01 0f 00 00 00 00 00 01 0a 01 01 01 01 0f 00 00 00 00 00
wlan0: Event ASSOC (0) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: associated
STA included RSN IE in (Re)AssocReq
  New STA
ap_sta_add: register ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffff1 authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 1 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ab4c0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
IEEE 802.1X: Ignore STA - 802.1X not enabled or forced for WPS
wlan0: STA XX:XX:XX:XX:XX:XX WPA: start authentication
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ab4c0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
WPA: XX:XX:XX:XX:XX:XX WPA_PTK_GROUP entering state IDLE
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION2
WPA: Re-initialize GMK/Counter on first station
Get randomness: len=32 entropy=1
GMK - hexdump(len=32): [REMOVED]
Get randomness: len=32 entropy=0
Key Counter - hexdump(len=32): [REMOVED]
Get randomness: len=32 entropy=0
GTK - hexdump(len=32): [REMOVED]
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=2 addr=0xaaaae74752b0 key_idx=1 set_tx=1 seq_len=0 key_len=32
nl80211: KEY_DATA - hexdump(len=32): [REMOVED]
   broadcast key
Get randomness: len=32 entropy=0
WPA: Assign ANonce - hexdump(len=32): 6a b9 dd 6f 9b 3f 9a 19 e5 ed f1 0f bf fd 39 c0 6b d0 59 53 f8 42 df a0 e6 91 fb 20 55 05 08 d7
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITPSK
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKSTART
wlan0: STA XX:XX:XX:XX:XX:XX WPA: sending 1/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=0 mic=0 ack=1 install=0 pairwise=1 kde_len=0 keyidx=0 encr=0)
WPA: Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
WPA: Use EAPOL-Key timeout of 1000 ms (retry counter 1)
wlan0: hostapd_new_assoc_sta: reschedule ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
nl80211: Event message available
nl80211: Drv Event 20 (NL80211_CMD_DEL_STATION) received for wlan0
nl80211: Delete station XX:XX:XX:XX:XX:XX
wlan0: Event DISASSOC (1) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: disassociated
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 2 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ab4c0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state DISCONNECTED
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ab4c0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x0 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
nl80211: sta_remove -> DEL_STATION wlan0 XX:XX:XX:XX:XX:XX --> 0 (Success)
hostapd_ht_operation_update current operation mode=0x0
hostapd_ht_operation_update new operation mode=0x0 changes=0
ap_free_sta: cancel ap_handle_timer for XX:XX:XX:XX:XX:XX
nl80211: Event message available
nl80211: Drv Event 19 (NL80211_CMD_NEW_STATION) received for wlan0
nl80211: New station XX:XX:XX:XX:XX:XX
nl80211: Assoc Req IEs - hexdump(len=175): 00 06 4d 79 53 53 49 44 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 21 02 03 14 24 02 01 0d 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00 2d 1a ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7f 08 00 00 08 00 00 00 00 40 dd 1e 00 90 4c 33 ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 dd 09 00 10 18 02 00 00 10 00 00 dd 07 00 50 f2 02 00 01 00 dd 1d 00 90 4c 5c 02 01 0a 00 08 07 01 0f 00 00 00 00 00 01 0a 01 01 01 01 0f 00 00 00 00 00
wlan0: Event ASSOC (0) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: associated
STA included RSN IE in (Re)AssocReq
  New STA
ap_sta_add: register ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffff1 authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 1 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ab7b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
IEEE 802.1X: Ignore STA - 802.1X not enabled or forced for WPS
wlan0: STA XX:XX:XX:XX:XX:XX WPA: start authentication
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ab7b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
WPA: XX:XX:XX:XX:XX:XX WPA_PTK_GROUP entering state IDLE
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION2
Get randomness: len=32 entropy=1
WPA: Assign ANonce - hexdump(len=32): 79 e8 0e 49 6a 56 0d 46 2a c8 4d 21 a8 70 ee ba 13 8e 17 ee 37 3b 69 e8 f9 ea 0c 6c 49 15 12 41
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITPSK
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKSTART
wlan0: STA XX:XX:XX:XX:XX:XX WPA: sending 1/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=0 mic=0 ack=1 install=0 pairwise=1 kde_len=0 keyidx=0 encr=0)
WPA: Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
WPA: Use EAPOL-Key timeout of 1000 ms (retry counter 1)
wlan0: hostapd_new_assoc_sta: reschedule ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
nl80211: Event message available
nl80211: Drv Event 20 (NL80211_CMD_DEL_STATION) received for wlan0
nl80211: Delete station XX:XX:XX:XX:XX:XX
wlan0: Event DISASSOC (1) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: disassociated
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 2 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ab7b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state DISCONNECTED
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ab7b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x0 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
nl80211: sta_remove -> DEL_STATION wlan0 XX:XX:XX:XX:XX:XX --> 0 (Success)
hostapd_ht_operation_update current operation mode=0x0
hostapd_ht_operation_update new operation mode=0x0 changes=0
ap_free_sta: cancel ap_handle_timer for XX:XX:XX:XX:XX:XX
nl80211: Event message available
nl80211: Drv Event 19 (NL80211_CMD_NEW_STATION) received for wlan0
nl80211: New station XX:XX:XX:XX:XX:XX
nl80211: Assoc Req IEs - hexdump(len=175): 00 06 4d 79 53 53 49 44 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 21 02 03 14 24 02 01 0d 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00 2d 1a ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7f 08 00 00 08 00 00 00 00 40 dd 1e 00 90 4c 33 ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 dd 09 00 10 18 02 00 00 10 00 00 dd 07 00 50 f2 02 00 01 00 dd 1d 00 90 4c 5c 02 01 0a 00 08 07 01 0f 00 00 00 00 00 01 0a 01 01 01 01 0f 00 00 00 00 00
wlan0: Event ASSOC (0) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: associated
STA included RSN IE in (Re)AssocReq
  New STA
ap_sta_add: register ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffff1 authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 1 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164abaa0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
IEEE 802.1X: Ignore STA - 802.1X not enabled or forced for WPS
wlan0: STA XX:XX:XX:XX:XX:XX WPA: start authentication
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164abaa0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
WPA: XX:XX:XX:XX:XX:XX WPA_PTK_GROUP entering state IDLE
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION2
Get randomness: len=32 entropy=1
WPA: Assign ANonce - hexdump(len=32): 9b 0d 6a 31 e5 21 2e 6a d5 cc f0 85 cc 9e d9 ff 07 79 4f 00 15 2a d3 04 2e 7b c5 54 13 36 d7 09
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITPSK
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKSTART
wlan0: STA XX:XX:XX:XX:XX:XX WPA: sending 1/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=0 mic=0 ack=1 install=0 pairwise=1 kde_len=0 keyidx=0 encr=0)
WPA: Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
WPA: Use EAPOL-Key timeout of 1000 ms (retry counter 1)
wlan0: hostapd_new_assoc_sta: reschedule ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
nl80211: Event message available
nl80211: Drv Event 20 (NL80211_CMD_DEL_STATION) received for wlan0
nl80211: Delete station XX:XX:XX:XX:XX:XX
wlan0: Event DISASSOC (1) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: disassociated
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 2 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164abaa0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state DISCONNECTED
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164abaa0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x0 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
nl80211: sta_remove -> DEL_STATION wlan0 XX:XX:XX:XX:XX:XX --> 0 (Success)
hostapd_ht_operation_update current operation mode=0x0
hostapd_ht_operation_update new operation mode=0x0 changes=0
ap_free_sta: cancel ap_handle_timer for XX:XX:XX:XX:XX:XX
nl80211: Event message available
nl80211: Drv Event 19 (NL80211_CMD_NEW_STATION) received for wlan0
nl80211: New station XX:XX:XX:XX:XX:XX
nl80211: Assoc Req IEs - hexdump(len=175): 00 06 4d 79 53 53 49 44 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 21 02 03 14 24 02 01 0d 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00 2d 1a ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7f 08 00 00 08 00 00 00 00 40 dd 1e 00 90 4c 33 ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 dd 09 00 10 18 02 00 00 10 00 00 dd 07 00 50 f2 02 00 01 00 dd 1d 00 90 4c 5c 02 01 0a 00 08 07 01 0f 00 00 00 00 00 01 0a 01 01 01 01 0f 00 00 00 00 00
wlan0: Event ASSOC (0) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: associated
STA included RSN IE in (Re)AssocReq
  New STA
ap_sta_add: register ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffff1 authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 1 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164abd90 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
IEEE 802.1X: Ignore STA - 802.1X not enabled or forced for WPS
wlan0: STA XX:XX:XX:XX:XX:XX WPA: start authentication
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164abd90 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
WPA: XX:XX:XX:XX:XX:XX WPA_PTK_GROUP entering state IDLE
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION2
Get randomness: len=32 entropy=1
WPA: Assign ANonce - hexdump(len=32): f5 8e 58 f0 6d 2c a5 ec b0 1e 86 4c be bc 56 d2 5f ee 54 82 cf 08 03 a1 e7 aa 58 c7 2c bc 72 f1
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITPSK
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKSTART
wlan0: STA XX:XX:XX:XX:XX:XX WPA: sending 1/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=0 mic=0 ack=1 install=0 pairwise=1 kde_len=0 keyidx=0 encr=0)
WPA: Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
WPA: Use EAPOL-Key timeout of 1000 ms (retry counter 1)
wlan0: hostapd_new_assoc_sta: reschedule ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
nl80211: Event message available
nl80211: Drv Event 20 (NL80211_CMD_DEL_STATION) received for wlan0
nl80211: Delete station XX:XX:XX:XX:XX:XX
wlan0: Event DISASSOC (1) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: disassociated
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 2 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164abd90 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state DISCONNECTED
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164abd90 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x0 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
nl80211: sta_remove -> DEL_STATION wlan0 XX:XX:XX:XX:XX:XX --> 0 (Success)
hostapd_ht_operation_update current operation mode=0x0
hostapd_ht_operation_update new operation mode=0x0 changes=0
ap_free_sta: cancel ap_handle_timer for XX:XX:XX:XX:XX:XX
nl80211: Event message available
nl80211: Drv Event 19 (NL80211_CMD_NEW_STATION) received for wlan0
nl80211: New station XX:XX:XX:XX:XX:XX
nl80211: Assoc Req IEs - hexdump(len=175): 00 06 4d 79 53 53 49 44 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 21 02 03 14 24 02 01 0d 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00 2d 1a ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7f 08 00 00 08 00 00 00 00 40 dd 1e 00 90 4c 33 ad 01 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 dd 09 00 10 18 02 00 00 10 00 00 dd 07 00 50 f2 02 00 01 00 dd 1d 00 90 4c 5c 02 01 0a 00 08 07 01 0f 00 00 00 00 00 01 0a 01 01 01 01 0f 00 00 00 00 00
wlan0: Event ASSOC (0) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: associated
STA included RSN IE in (Re)AssocReq
  New STA
ap_sta_add: register ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffff1 authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 1 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ac5b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
IEEE 802.1X: Ignore STA - 802.1X not enabled or forced for WPS
wlan0: STA XX:XX:XX:XX:XX:XX WPA: start authentication
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ac5b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x60 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
WPA: XX:XX:XX:XX:XX:XX WPA_PTK_GROUP entering state IDLE
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state AUTHENTICATION2
Get randomness: len=32 entropy=1
WPA: Assign ANonce - hexdump(len=32): 49 b5 a5 de 09 86 ae 7d 24 89 59 1a 01 0d 5e 90 aa ba ec 84 bf 8c d7 40 3a 56 d9 d7 92 b9 01 72
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITPSK
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKSTART
wlan0: STA XX:XX:XX:XX:XX:XX WPA: sending 1/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=0 mic=0 ack=1 install=0 pairwise=1 kde_len=0 keyidx=0 encr=0)
WPA: Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
WPA: Use EAPOL-Key timeout of 1000 ms (retry counter 1)
wlan0: hostapd_new_assoc_sta: reschedule ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (300 seconds - ap_max_inactivity)
wlan0: STA XX:XX:XX:XX:XX:XX WPA: EAPOL-Key timeout
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKSTART
wlan0: STA XX:XX:XX:XX:XX:XX WPA: sending 1/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=0 mic=0 ack=1 install=0 pairwise=1 kde_len=0 keyidx=0 encr=0)
WPA: Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 02
WPA: Use EAPOL-Key timeout of 1000 ms (retry counter 2)
wlan0: STA XX:XX:XX:XX:XX:XX WPA: EAPOL-Key timeout
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKSTART
wlan0: STA XX:XX:XX:XX:XX:XX WPA: sending 1/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=0 mic=0 ack=1 install=0 pairwise=1 kde_len=0 keyidx=0 encr=0)
WPA: Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 03
WPA: Use EAPOL-Key timeout of 1000 ms (retry counter 3)
wlan0: Event EAPOL_RX (23) received
IEEE 802.1X: 121 bytes from XX:XX:XX:XX:XX:XX
   IEEE 802.1X: version=1 type=3 length=117
WPA: RX EAPOL data - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 56 5d 36 ca 7f cf d8 66 2e 9c 83 cd 64 2b b5 6b 00 16 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00
WPA: Received EAPOL-Key from XX:XX:XX:XX:XX:XX key_info=0x10a type=2 mic_len=16 key_data_length=22
WPA: EAPOL-Key header (ending before Key MIC) - hexdump(len=77): 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Key MIC - hexdump(len=16): 56 5d 36 ca 7f cf d8 66 2e 9c 83 cd 64 2b b5 6b
WPA: Received Key Nonce - hexdump(len=32): 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b
WPA: Received Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: STA XX:XX:XX:XX:XX:XX WPA: received EAPOL-Key frame (2/4 Pairwise)
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKCALCNEGOTIATING
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=(nil)
WPA: PTK derivation using PRF(SHA1)
WPA: PTK derivation - A1=aa:bb:cc:dd:ee:ff A2=XX:XX:XX:XX:XX:XX
WPA: Nonce1 - hexdump(len=32): 49 b5 a5 de 09 86 ae 7d 24 89 59 1a 01 0d 5e 90 aa ba ec 84 bf 8c d7 40 3a 56 d9 d7 92 b9 01 72
WPA: Nonce2 - hexdump(len=32): 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=48): [REMOVED]
WPA: KCK - hexdump(len=16): [REMOVED]
WPA: KEK - hexdump(len=16): [REMOVED]
WPA: TK - hexdump(len=16): [REMOVED]
WPA: EAPOL-Key MIC using HMAC-SHA1
Searching a PSK for XX:XX:XX:XX:XX:XX prev_psk=0xaaab164a634c
wlan0: STA XX:XX:XX:XX:XX:XX WPA: invalid MIC in msg 2/4 of 4-Way Handshake
wlan0: AP-STA-POSSIBLE-PSK-MISMATCH XX:XX:XX:XX:XX:XX
wlan0: Event EAPOL_RX (23) received
IEEE 802.1X: 121 bytes from XX:XX:XX:XX:XX:XX
   IEEE 802.1X: version=1 type=3 length=117
WPA: RX EAPOL data - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 4e b4 d9 1d cf 2f fd 99 8d 61 ff 2e fe 1b 9e 67 00 16 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00
WPA: Received EAPOL-Key from XX:XX:XX:XX:XX:XX key_info=0x10a type=2 mic_len=16 key_data_length=22
WPA: EAPOL-Key header (ending before Key MIC) - hexdump(len=77): 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Key MIC - hexdump(len=16): 4e b4 d9 1d cf 2f fd 99 8d 61 ff 2e fe 1b 9e 67
WPA: Received Key Nonce - hexdump(len=32): 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b
WPA: Received Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: STA XX:XX:XX:XX:XX:XX WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
received replay counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: Event EAPOL_RX (23) received
IEEE 802.1X: 121 bytes from XX:XX:XX:XX:XX:XX
   IEEE 802.1X: version=1 type=3 length=117
WPA: RX EAPOL data - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a0 c2 1e 2d 93 0c d8 7f 2c 47 87 94 86 11 d4 42 00 16 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00
WPA: Received EAPOL-Key from XX:XX:XX:XX:XX:XX key_info=0x10a type=2 mic_len=16 key_data_length=22
WPA: EAPOL-Key header (ending before Key MIC) - hexdump(len=77): 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Key MIC - hexdump(len=16): a0 c2 1e 2d 93 0c d8 7f 2c 47 87 94 86 11 d4 42
WPA: Received Key Nonce - hexdump(len=32): 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b
WPA: Received Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: STA XX:XX:XX:XX:XX:XX WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
received replay counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: Event EAPOL_RX (23) received
IEEE 802.1X: 121 bytes from XX:XX:XX:XX:XX:XX
   IEEE 802.1X: version=1 type=3 length=117
WPA: RX EAPOL data - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 21 84 8e a7 9c 34 7c bb de ba 3b a9 d5 6d ed 31 00 16 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00
WPA: Received EAPOL-Key from XX:XX:XX:XX:XX:XX key_info=0x10a type=2 mic_len=16 key_data_length=22
WPA: EAPOL-Key header (ending before Key MIC) - hexdump(len=77): 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Key MIC - hexdump(len=16): 21 84 8e a7 9c 34 7c bb de ba 3b a9 d5 6d ed 31
WPA: Received Key Nonce - hexdump(len=32): 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b
WPA: Received Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: STA XX:XX:XX:XX:XX:XX WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
received replay counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: Event EAPOL_RX (23) received
IEEE 802.1X: 121 bytes from XX:XX:XX:XX:XX:XX
   IEEE 802.1X: version=1 type=3 length=117
WPA: RX EAPOL data - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 68 5b 26 49 a1 99 97 cf 93 f8 07 ff b3 dc 48 03 00 16 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00
WPA: Received EAPOL-Key from XX:XX:XX:XX:XX:XX key_info=0x10a type=2 mic_len=16 key_data_length=22
WPA: EAPOL-Key header (ending before Key MIC) - hexdump(len=77): 02 01 0a 00 00 00 00 00 00 00 00 00 01 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Key MIC - hexdump(len=16): 68 5b 26 49 a1 99 97 cf 93 f8 07 ff b3 dc 48 03
WPA: Received Key Nonce - hexdump(len=32): 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b
WPA: Received Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: STA XX:XX:XX:XX:XX:XX WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
received replay counter - hexdump(len=8): 00 00 00 00 00 00 00 01
wlan0: Event EAPOL_RX (23) received
IEEE 802.1X: 121 bytes from XX:XX:XX:XX:XX:XX
   IEEE 802.1X: version=1 type=3 length=117
WPA: RX EAPOL data - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 02 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f9 93 55 1d 50 6a f0 66 c1 db e9 3f 28 a2 5a ac 00 16 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00
WPA: Received EAPOL-Key from XX:XX:XX:XX:XX:XX key_info=0x10a type=2 mic_len=16 key_data_length=22
WPA: EAPOL-Key header (ending before Key MIC) - hexdump(len=77): 02 01 0a 00 00 00 00 00 00 00 00 00 02 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Key MIC - hexdump(len=16): f9 93 55 1d 50 6a f0 66 c1 db e9 3f 28 a2 5a ac
WPA: Received Key Nonce - hexdump(len=32): 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b
WPA: Received Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 02
wlan0: STA XX:XX:XX:XX:XX:XX WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
received replay counter - hexdump(len=8): 00 00 00 00 00 00 00 02
wlan0: Event EAPOL_RX (23) received
IEEE 802.1X: 121 bytes from XX:XX:XX:XX:XX:XX
   IEEE 802.1X: version=1 type=3 length=117
WPA: RX EAPOL data - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 03 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 d4 77 41 dd 7f 7f 8d d2 4a 45 0c 9f 50 78 57 a6 00 16 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 80 00
WPA: Received EAPOL-Key from XX:XX:XX:XX:XX:XX key_info=0x10a type=2 mic_len=16 key_data_length=22
WPA: EAPOL-Key header (ending before Key MIC) - hexdump(len=77): 02 01 0a 00 00 00 00 00 00 00 00 00 03 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: EAPOL-Key Key MIC - hexdump(len=16): d4 77 41 dd 7f 7f 8d d2 4a 45 0c 9f 50 78 57 a6
WPA: Received Key Nonce - hexdump(len=32): 60 8c cf b4 28 77 a1 6b d4 61 ad 46 76 29 a7 ee e8 9d 92 8c b7 74 66 82 b0 c3 8b 40 2e c5 62 7b
WPA: Received Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 03
wlan0: STA XX:XX:XX:XX:XX:XX WPA: received EAPOL-Key 2/4 Pairwise with unexpected replay counter
received replay counter - hexdump(len=8): 00 00 00 00 00 00 00 03
wlan0: STA XX:XX:XX:XX:XX:XX WPA: EAPOL-Key timeout
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKSTART
wlan0: STA XX:XX:XX:XX:XX:XX WPA: sending 1/4 msg of 4-Way Handshake
WPA: Send EAPOL(version=2 secure=0 mic=0 ack=1 install=0 pairwise=1 kde_len=0 keyidx=0 encr=0)
WPA: Replay Counter - hexdump(len=8): 00 00 00 00 00 00 00 04
WPA: Use EAPOL-Key timeout of 1000 ms (retry counter 4)
wlan0: STA XX:XX:XX:XX:XX:XX WPA: EAPOL-Key timeout
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state PTKSTART
wlan0: STA XX:XX:XX:XX:XX:XX WPA: PTKSTART: Retry limit 4 reached
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state DISCONNECT
wpa_sta_disconnect STA XX:XX:XX:XX:XX:XX (reason 2)
hostapd_wpa_auth_disconnect: WPA authenticator requests disconnect: STA XX:XX:XX:XX:XX:XX reason 2
wlan0: ap_sta_disconnect addr XX:XX:XX:XX:XX:XX reason=2
nl80211: sta_remove -> DEL_STATION wlan0 XX:XX:XX:XX:XX:XX --> 0 (Success)
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 3 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ac5b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
wlan0: ap_sta_disconnect: reschedule ap_handle_timer timeout for XX:XX:XX:XX:XX:XX (5 seconds - AP_MAX_INACTIVITY_AFTER_DEAUTH)
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state DISCONNECTED
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ac5b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x0 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
wlan0: Deauthentication callback for STA XX:XX:XX:XX:XX:XX
wlan0: Removing STA XX:XX:XX:XX:XX:XX from kernel driver
nl80211: sta_remove -> DEL_STATION wlan0 XX:XX:XX:XX:XX:XX --> 0 (Success)
wlan0: STA XX:XX:XX:XX:XX:XX MLME: MLME-DEAUTHENTICATE.indication(XX:XX:XX:XX:XX:XX, 2)
wlan0: STA XX:XX:XX:XX:XX:XX MLME: MLME-DELETEKEYS.request(XX:XX:XX:XX:XX:XX)
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ac5b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Event message available
nl80211: Drv Event 20 (NL80211_CMD_DEL_STATION) received for wlan0
nl80211: Delete station XX:XX:XX:XX:XX:XX
wlan0: Event DISASSOC (1) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: disassociated
wlan0: STA XX:XX:XX:XX:XX:XX WPA: event 2 notification
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ac5b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state DISCONNECTED
WPA: XX:XX:XX:XX:XX:XX WPA_PTK entering state INITIALIZE
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=0xaaab164ac5b0 key_idx=0 set_tx=1 seq_len=0 key_len=0
   addr=XX:XX:XX:XX:XX:XX
nl80211: set_key failed; err=-22 Invalid argument)
RSN: PTK removal from the driver failed
nl80211: Set STA flags - ifname=wlan0 addr=XX:XX:XX:XX:XX:XX total_flags=0x0 flags_or=0x0 flags_and=0xfffffffe authorized=0
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.1X: unauthorizing port
nl80211: sta_remove -> DEL_STATION wlan0 XX:XX:XX:XX:XX:XX --> 0 (Success)
hostapd_ht_operation_update current operation mode=0x0
hostapd_ht_operation_update new operation mode=0x0 changes=0
ap_free_sta: cancel ap_handle_timer for XX:XX:XX:XX:XX:XX
nl80211: Event message available
nl80211: Drv Event 20 (NL80211_CMD_DEL_STATION) received for wlan0
nl80211: Delete station XX:XX:XX:XX:XX:XX
wlan0: Event DISASSOC (1) received
wlan0: STA XX:XX:XX:XX:XX:XX IEEE 802.11: disassociated
Disassociation notification for unknown STA XX:XX:XX:XX:XX:XX
Signal 2 received - terminating
hostapd_interface_deinit_free(0xaaab164a25b0)
hostapd_interface_deinit_free: num_bss=1 conf->num_bss=1
hostapd_interface_deinit(0xaaab164a25b0)
wlan0: interface state ENABLED->DISABLED
hostapd_bss_deinit: deinit bss wlan0
wlan0: Deauthenticate all stations
nl80211: sta_remove -> DEL_STATION wlan0 ff:ff:ff:ff:ff:ff --> 0 (Success)
wlan0: AP-DISABLED 
hostapd_cleanup(hapd=0xaaab164a3c00 (wlan0))
wlan0: CTRL-EVENT-TERMINATING 
hostapd_free_hapd_data(wlan0)
hostapd_interface_deinit_free: driver=0xaaaae750c678 drv_priv=0xaaab164a4ec0 -> hapd_deinit
nl80211: deinit ifname=wlan0 disabled_11b_rates=0
nl80211: Disable Probe Request reporting nl_preq=0x888822239ec229e9
nl80211: Remove monitor interface: refcount=0
nl80211: Remove beacon (ifindex=4)
netlink: Operstate: ifindex=4 linkmode=0 (kernel-control), operstate=6 (IF_OPER_UP)
nl80211: Set mode ifindex 4 iftype 2 (STATION)
nl80211: Teardown AP(wlan0) - device_ap_sme=1 use_monitor=0
nl80211: Unsubscribe mgmt frames handle 0x888822239ec2dfa9 (AP teardown (dev SME))
hostapd_interface_free(0xaaab164a25b0)
hostapd_interface_free: free hapd 0xaaab164a3c00
hostapd_cleanup_iface(0xaaab164a25b0)
hostapd_cleanup_iface_partial(0xaaab164a25b0)
hostapd_cleanup_iface: free iface=0xaaab164a25b0
```

---

### Post by dony71 on 2021-01-13
I'm using Ubuntu 20.04 server on my Raspbery Pi 4 and I get same issue
How to resolved this issue?

---

### Post by QIII on 2021-01-13
Hello.

Please start your own thread and describe your symptoms rather than attempting to raise an old thread from the dead.

Thanks.

Closed.

---

