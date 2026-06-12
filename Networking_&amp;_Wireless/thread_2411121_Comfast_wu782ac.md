---
title: "Comfast wu782ac"
date: 2019-01-25
forum: Networking &amp; Wireless
---

### Post by rekikn12 on 2019-01-25
Hi everyone. How are us?. 
I come to write here because i have problems with the comfast wu782ac usb wifi. I have Ubuntu server 17.10 installed in my pc, and following this guides i can install the drivers.
[https://github.com/ulli-kroll/mt7612u/issues/27#issuecomment-338138025](https://github.com/ulli-kroll/mt7612u/issues/27#issuecomment-338138025)
[https://github.com/genodeftest/Netgear-A6210/tree/4.13-fix-only](https://github.com/genodeftest/Netgear-A6210/tree/4.13-fix-only)

But i wish create an AP with this network adapter, And trying with hostapd i can't make the AP wifi.

Can someone help me please :<

```

[COLOR=#000000][FONT=Menlo]root@Yui:~# cat hostapd.conf [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]### Configuraciones que hace el conect_ap ###[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]beacon_int=100[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ap_isolate=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#ht_capab=[HT40+][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#wmm_enabled=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]country_code=US[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]### Wireless network name ###[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]interface=wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]### Set your bridge name ###[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]bridge=br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]### Set driver ###[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#driver=mt7662u_sta[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]driver=nl80211[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]### Configuraciones de normas y velocidades ###[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# a simply means 2.5GHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]hw_mode=g[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# the channel to use, 0 means the AP will search for the channel with the least interferences [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]channel=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# limit the frequencies used to those allowed in the country[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ieee80211d=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# 802.11n support[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ieee80211n=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#ieee80211ac=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#require_ht=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]#require_vht=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# QoS support[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wmm_enabled=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## Shared Key Authentication ##[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]macaddr_acl=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## Accept all MAC address ###[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]auth_algs=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]## Configuracion de la red ###[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ssid=TESTAP[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ignore_broadcast_ssid=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa=3[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_passphrase=1234567890[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_key_mgmt=WPA-PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_pairwise=TKIP CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]rsn_pairwise=CCMP[/FONT][/COLOR]

```

```

[COLOR=#000000][FONT=Menlo]root@Yui:~# sudo hostapd -d hostapd.conf [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]random: Trying to read entropy from /dev/random[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Configuration file: hostapd.conf[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]rfkill: initial event: idx=0 type=1 op=0 soft=0 hard=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Supported cipher 00-0f-ac:1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Supported cipher 00-0f-ac:5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Supported cipher 00-0f-ac:2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Supported cipher 00-0f-ac:4[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Disable use_monitor with device_ap_sme since no monitor mode support detected[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: interface wlan0 in phy phy0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Set mode ifindex 4 iftype 3 (AP)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Setup AP(wlan0) - device_ap_sme=1 use_monitor=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Subscribe to mgmt frames with AP handle 0x5610ad146be0 (device SME)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x5610ad146be0 match=[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Enable Probe Request reporting nl_preq=0x5610ad14c7d0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Register frame type=0x40 (WLAN_FC_STYPE_PROBE_REQ) nl_handle=0x5610ad14c7d0 match=[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: if_indices[16]: 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 4[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: if_indices[16]: 5 4[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Adding interface wlan0 into bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]phy: phy0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]BSS count 1, BSSID mask 00:00:00:00:00:00 (0 bits)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: interface state UNINITIALIZED->COUNTRY_UPDATE[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Previous country code US, new country code US [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Regulatory information - country=US (DFS-FCC)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: 2402-2472 @ 40 MHz 30 mBm[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: 5170-5250 @ 80 MHz 23 mBm[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: 5250-5330 @ 80 MHz 23 mBm (DFS)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: 5490-5730 @ 160 MHz 23 mBm (DFS)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: 5735-5835 @ 80 MHz 30 mBm[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: 57240-63720 @ 2160 MHz 40 mBm[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Added 802.11b mode based on 802.11g information[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]hw vht capab: 0x0, conf vht capab: 0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Completing interface initialization[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Mode: IEEE 802.11g  Channel: 1  Frequency: 2412 MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]DFS 0 channels required radar detection[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Set freq 2412 (ht_enabled=1, vht_enabled=0, bandwidth=20 MHz, cf1=2412 MHz, cf2=0 MHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  * freq=2412[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  * vht_enabled=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  * ht_enabled=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  * sec_channel_offset=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  * channel_type=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[0] rate=10 flags=0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[1] rate=20 flags=0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[2] rate=55 flags=0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[3] rate=110 flags=0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[4] rate=60 flags=0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[5] rate=90 flags=0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[6] rate=120 flags=0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[7] rate=180 flags=0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[8] rate=240 flags=0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[9] rate=360 flags=0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[10] rate=480 flags=0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RATE[11] rate=540 flags=0x0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]hostapd_setup_bss(hapd=0x5610ad145ff0 (wlan0), first=1)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: Flushing old station entries[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: flush -> DEL_STATION wlan0 (all)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: Deauthenticate all stations[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: sta_remove -> DEL_STATION wlan0 ff:ff:ff:ff:ff:ff --> 0 (Success)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=0 set_tx=0 seq_len=0 key_len=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=1 set_tx=0 seq_len=0 key_len=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=2 set_tx=0 seq_len=0 key_len=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=3 set_tx=0 seq_len=0 key_len=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Using interface wlan0 with hwaddr 40:a5:ef:4e:c9:23 and ssid "Depto602Prueba"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Deriving WPA PSK based on passphrase[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]SSID - hexdump_ascii(len=14):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]     44 65 70 74 6f 36 30 32 50 72 75 65 62 61         Depto602Prueba  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]PSK (from passphrase) - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]random: Got 20/20 bytes from /dev/random[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GMK - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Key Counter - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]WPA: Delay group state machine start until Beacon frames have been configured[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Set beacon (beacon_set=0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Beacon head - hexdump(len=65): 80 00 00 00 ff ff ff ff ff ff 40 a5 ef 4e c9 23 40 a5 ef 4e c9 23 00 00 00 00 00 00 00 00 00 00 64 00 11 04 00 0e 44 65 70 74 6f 36 30 32 50 72 75 65 62 61 01 08 82 84 8b 96 0c 12 18 24 03 01 01[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Beacon tail - hexdump(len=151): 07 06 55 53 20 01 0b 1e 2a 01 04 32 04 30 48 60 6c 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 0c 00 dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02 2d 1a 0c 00 13 ff ff 00 00 01 00 00 00 00 00 2c 01 01 00 00 00 00 00 00 00 00 00 00 3d 16 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7f 04 00 00 00 02 dd 18 00 50 f2 02 01 01 00 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex=4[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: beacon_int=100[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: dtim_period=2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ssid - hexdump_ascii(len=14):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]     44 65 70 74 6f 36 30 32 50 72 75 65 62 61         Depto602Prueba  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  * beacon_int=100[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: hidden SSID not in use[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: privacy=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: auth_algs=0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: wpa_version=0x3[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: key_mgmt_suites=0x2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: pairwise_ciphers=0x18[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: group_cipher=0x8[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: SMPS mode - off[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: beacon_ies - hexdump(len=6): 7f 04 00 00 00 02[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: proberesp_ies - hexdump(len=6): 7f 04 00 00 00 02[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: assocresp_ies - hexdump(len=6): 7f 04 00 00 00 02[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ap_max_inactivity=300[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]WPA: Start group state machine to set initial keys[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]WPA: group state machine entering state GTK_INIT (VLAN-ID 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GTK - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]WPA: group state machine entering state SETKEYSDONE (VLAN-ID 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=2 addr=0x5610ab8a08c9 key_idx=1 set_tx=1 seq_len=0 key_len=32[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: KEY_DATA - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   broadcast key[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Set wlan0 operstate 0->1 (UP)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]netlink: Operstate: ifindex=4 linkmode=-1 (no change), operstate=6 (IF_OPER_UP)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Failed to set TX queue parameters for queue 0.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Failed to set TX queue parameters for queue 1.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Failed to set TX queue parameters for queue 2.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Failed to set TX queue parameters for queue 3.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: interface state COUNTRY_UPDATE->ENABLED[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: AP-ENABLED [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: Setup of interface done.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ctrl_iface not configured![/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 operstate=2 linkmode=0 ifi_family=0 ifi_flags=0x11003 ([UP][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Set IF_OPER_UP again based on ifi_flags and expected operstate[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]netlink: Operstate: ifindex=4 linkmode=-1 (no change), operstate=6 (IF_OPER_UP)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 wext ifi_family=0 ifi_flags=0x1002 ()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Ignore interface down event since interface wlan0 is up[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 operstate=6 linkmode=0 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 operstate=6 linkmode=0 master=5 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=6 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=6 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=6 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=5 ifname=br0 operstate=6 linkmode=0 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: Event INTERFACE_STATUS (5) received[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Unknown event 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Drv Event 16 (NL80211_CMD_STOP_AP) received for wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: Event INTERFACE_UNAVAILABLE (29) received[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Interface wlan0 is unavailable -- stopped[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 operstate=2 linkmode=0 master=5 ifi_family=0 ifi_flags=0x1002 ()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Interface down (wlan0/wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: Event INTERFACE_DISABLED (27) received[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: INTERFACE-DISABLED [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=0 ifi_flags=0x1002 ()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=0 ifi_flags=0x1003 ([UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 wext ifi_family=0 ifi_flags=0x1003 ([UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Ignore interface up event since interface wlan0 is down[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=2 ifi_family=7 ifi_flags=0x1002 ()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=2 ifi_family=7 ifi_flags=0x1002 ()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=7 ifi_flags=0x1002 ()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=7 ifi_flags=0x1002 ()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 operstate=2 linkmode=0 master=5 ifi_family=0 ifi_flags=0x11003 ([UP][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Interface up[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: Event INTERFACE_ENABLED (26) received[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: INTERFACE-ENABLED [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=2 addr=0x5610ab8a08c9 key_idx=1 set_tx=1 seq_len=0 key_len=32[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: KEY_DATA - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   broadcast key[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Set beacon (beacon_set=0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Beacon head - hexdump(len=65): 80 00 00 00 ff ff ff ff ff ff 40 a5 ef 4e c9 23 40 a5 ef 4e c9 23 00 00 00 00 00 00 00 00 00 00 64 00 11 04 00 0e 44 65 70 74 6f 36 30 32 50 72 75 65 62 61 01 08 82 84 8b 96 0c 12 18 24 03 01 01[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Beacon tail - hexdump(len=151): 07 06 55 53 20 01 0b 1e 2a 01 04 32 04 30 48 60 6c 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 0c 00 dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02 2d 1a 0c 00 13 ff ff 00 00 01 00 00 00 00 00 2c 01 01 00 00 00 00 00 00 00 00 00 00 3d 16 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 7f 04 00 00 00 02 dd 18 00 50 f2 02 01 01 00 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex=4[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: beacon_int=100[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: dtim_period=2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ssid - hexdump_ascii(len=14):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]     44 65 70 74 6f 36 30 32 50 72 75 65 62 61         Depto602Prueba  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  * beacon_int=100[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: hidden SSID not in use[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: privacy=1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: auth_algs=0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: wpa_version=0x3[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: key_mgmt_suites=0x2[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: pairwise_ciphers=0x18[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: group_cipher=0x8[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: SMPS mode - off[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: beacon_ies - hexdump(len=6): 7f 04 00 00 00 02[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: proberesp_ies - hexdump(len=6): 7f 04 00 00 00 02[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: assocresp_ies - hexdump(len=6): 7f 04 00 00 00 02[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ap_max_inactivity=300[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Set IF_OPER_UP again based on ifi_flags and expected operstate[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]netlink: Operstate: ifindex=4 linkmode=-1 (no change), operstate=6 (IF_OPER_UP)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 wext ifi_family=0 ifi_flags=0x1002 ()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Ignore interface down event since interface wlan0 is up[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=2 ifi_family=7 ifi_flags=0x11003 ([UP][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Set IF_OPER_UP again based on ifi_flags and expected operstate[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]netlink: Operstate: ifindex=4 linkmode=-1 (no change), operstate=6 (IF_OPER_UP)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=6 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=6 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=6 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 operstate=6 linkmode=0 master=5 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=0 ifi_flags=0x11003 ([UP][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=0 ifi_flags=0x1002 ()[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=7 ifi_flags=0x11003 ([UP][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RTM_NEWLINK: ifi_index=4 ifname=wlan0 master=5 operstate=6 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add ifindex 5 for bridge br0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: Add own interface ifindex 5[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: ifindex 5 already in the list[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=7 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]VLAN: vlan_newlink(wlan0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: WPA rekeying GTK[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]WPA: group state machine entering state SETKEYS (VLAN-ID 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GTK - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_group_setkeys: GKeyDoneStations=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]WPA: group state machine entering state SETKEYSDONE (VLAN-ID 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=2 addr=0x5610ab8a08c9 key_idx=2 set_tx=1 seq_len=0 key_len=32[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: KEY_DATA - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   broadcast key[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wlan0: WPA rekeying GTK[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]WPA: group state machine entering state SETKEYS (VLAN-ID 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]GTK - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_group_setkeys: GKeyDoneStations=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]WPA: group state machine entering state SETKEYSDONE (VLAN-ID 0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=2 addr=0x5610ab8a08c9 key_idx=1 set_tx=1 seq_len=0 key_len=32[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nl80211: KEY_DATA - hexdump(len=32): [REMOVED][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]   broadcast key[/FONT][/COLOR]

```

```

[COLOR=#000000][FONT=Menlo]root@Yui:~# dmesg -wH[/FONT][/COLOR]

```
[https://paste.ubuntu.com/p/zN2wdsJKkr/](https://paste.ubuntu.com/p/zN2wdsJKkr/)

---

### Post by praseodym on 2019-01-25
17.10 is end of life, isn't it? Upgrade to 18.04 and show the output of "lsusb"

---

### Post by coffeecat on 2019-01-25
@rekikn12, a comment about your use of BBCode.

You have used code tags correctly, but you have spoilt the contents of your code boxes by adding unnecessary font and colour tags. Dozens and dozens of them. It's such a mess I'm not even going to attempt to sort it out for you. Please simply use code tags alone, and the forum software will use the appropriate monospace font for preserving formatting.

And html BBCode tags. That's not what they are for. Html tags are for posting - well - html code, if you want someone to help you debug it. If you were trying to create hyperlinks, simply post the URL and the forum software will do the rest for you. By using html tags your links are not clickable which is inconvenient for forum members trying to help you.

---

### Post by rekikn12 on 2019-01-27
I upgrade to 18.04 and try with [https://github.com/kaduke/Netgear-A6210](https://github.com/kaduke/Netgear-A6210) with branch port-to-4.15 without lucky

This is the lsusb
Bus 005 Device 003: ID 0e8d:2870 MediaTek Inc.

But i can change the mode with this command
sudo usb_modeswitch -KW -v 0e8d -p 2870

and change to
Bus 006 Device 003: ID 0e8d:7612 MediaTek Inc. 

```

Take all parameters from the command line




 * usb_modeswitch: handle USB devices with multiple modes
 * Version 2.5.2 (C) Josua Dietze 2017
 * Based on libusb1/libusbx


 ! PLEASE REPORT NEW CONFIGURATIONS !


DefaultVendor=  0x0e8d
DefaultProduct= 0x2870


StandardEject=1


Look for default devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 0e8d:2870
   vendor ID matched
   product ID matched
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 1d6b:0002
 Found devices in default mode (1)
Access device 003 on bus 005
Get the current device configuration ...
Current configuration number is 1
Use interface number 0
 with class 8
Use endpoints 0x02 (out) and 0x82 (in)


USB description data (for identification)
-------------------------
Manufacturer: ?
     Product: ?
  Serial No.: ?
-------------------------
Sending standard EJECT sequence
Looking for active drivers ...
 OK, driver detached
Set up interface 0
Use endpoint 0x02 for message sending ...
Trying to send message 1 to endpoint 0x02 ...
 OK, message successfully sent
Read the response to message 1 (CSW) ...
 Response successfully read (0 bytes), status 0
Trying to send message 2 to endpoint 0x02 ...
 OK, message successfully sent
Read the response to message 2 (CSW) ...
 Response successfully read (13 bytes), status 0
Trying to send message 3 to endpoint 0x02 ...
 Sending the message returned error -1. Try to continue
Read the response to message 3 (CSW) ...
 Device seems to have vanished after reading. Good.
 Device is gone, skip any further commands
-> Run lsusb to note any changes. Bye!

```

---

### Post by praseodym on 2019-01-27
[https://github.com/jurobystricky/Netgear-A6210](https://github.com/jurobystricky/Netgear-A6210)

Try this one instead, uninstall the other first

---

### Post by praseodym on 2019-01-27
Edit: Works here, use the dkms installation

```
git clone https://github.com/jurobystricky/Netgear-A6210
sudo mv Netgear-A6210/ /usr/src/netgear-a6210-2.5.0
sudo dkms install netgear-a6210/2.5.0 
```
Run

```
sudo modprobe -v mt7662u_sta
```
```

modinfo mt7662u_sta
filename:       /lib/modules/4.4.0-141-generic/updates/dkms/mt7662u_sta.ko
version:        3.0.0.1
license:        GPL
description:    Ralink Wireless Lan Linux Driver
author:         Ralink
srcversion:     8D0D4E28D8944B7791A58D4
alias:          usb:v0E8Dp7662d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp7632d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp7612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v045Ep02E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17EBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p180Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9014d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
vermagic:       4.4.0-141-generic SMP mod_unload modversions retpoline 
parm:           mac:rt_wifi: wireless mac addr (charp)
parm:           mode:rt_wifi: wireless operation mode (charp)
```

---

### Post by rekikn12 on 2019-01-27
I tried with jurobystricky repo in my first tries but the drivers give me errors with the headers kernel.

Anyway, that is the out of ~$ sudo dkms install netgear-a6210/2.5.0
```

Creating symlink /var/lib/dkms/netgear-a6210/2.5.0/source ->
                 /usr/src/netgear-a6210-2.5.0


DKMS: add completed.


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area...(bad exit status: 2)
make -j2 KERNELRELEASE=4.15.0-43-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for netgear-a6210: 2.5.0 not found
Error! Bad return status for module build on kernel: 4.15.0-43-generic (x86_64)
Consult /var/lib/dkms/netgear-a6210/2.5.0/build/make.log for more information.

```

~$ cat /var/lib/dkms/netgear-a6210/2.5.0/build/make.log
```

DKMS make.log for netgear-a6210-2.5.0 for kernel 4.15.0-43-generic (x86_64)
dom ene 27 14:40:16 UTC 2019
export DBGFLAGS


*** Building driver with debug messages ***


cp -f os/linux/Makefile.6 /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/Makefile
make -C /lib/modules/4.15.0-43-generic/build DBGFLAGS=-DDBG SUBDIRS=/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-43-generic'
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/assoc.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/auth.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/auth_rsp.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/sync.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/sanity.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/rtmp_data.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/connect.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/wpa.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/sta_cfg.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../sta/sta.o
  CC [M]  /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.o
In file included from ./include/linux/bitmap.h:9:0,
                 from ./include/linux/cpumask.h:12,
                 from ./arch/x86/include/asm/cpumask.h:5,
                 from ./arch/x86/include/asm/msr.h:11,
                 from ./arch/x86/include/asm/processor.h:21,
                 from ./arch/x86/include/asm/cpufeature.h:5,
                 from ./arch/x86/include/asm/thread_info.h:53,
                 from ./include/linux/thread_info.h:38,
                 from ./arch/x86/include/asm/preempt.h:7,
                 from ./include/linux/preempt.h:81,
                 from ./include/linux/spinlock.h:51,
                 from ./include/linux/seqlock.h:36,
                 from ./include/linux/time.h:6,
                 from ./include/linux/stat.h:19,
                 from ./include/linux/module.h:10,
                 from /var/lib/dkms/netgear-a6210/2.5.0/build/include/os/rt_linux.h:14,
                 from /var/lib/dkms/netgear-a6210/2.5.0/build/include/rtmp_os.h:30,
                 from /var/lib/dkms/netgear-a6210/2.5.0/build/include/rtmp_comm.h:64,
                 from /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.c:33:
In function ‘memcpy’,
    inlined from ‘rt_ioctl_iwaplist’ at /var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.c:549:2:
./include/linux/string.h:340:4: error: call to ‘__read_overflow2’ declared with attribute error: detected read beyond size of object passed as 2nd parameter
    __read_overflow2();
    ^~~~~~~~~~~~~~~~~~
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.o' failed
make[2]: *** [/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux/../../os/linux/sta_ioctl.o] Error 1
make[2]: *** Waiting for unfinished jobs....
Makefile:1551: recipe for target '_module_/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux' failed
make[1]: *** [_module_/var/lib/dkms/netgear-a6210/2.5.0/build/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-43-generic'
Makefile:59: recipe for target 'debug' failed
make: *** [debug] Error 2

```

---

### Post by rekikn12 on 2019-01-27
I make a little progress

Making my own version of driver, applying the changes of other repos i can make this [https://bitbucket.org/rkkn/netgear-a6210/src/master/](https://bitbucket.org/rkkn/netgear-a6210/src/master/)

But, i can't make an AP yet. When try to create an AP, can't see the AP in another devices

~$ sudo modprobe -v mt7662u_sta
```

insmod /lib/modules/4.15.0-43-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/mt7662u_sta.ko 

```

~$ modinfo mt7662u_sta
```

filename:       /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/mt7662u_sta.ko
version:        3.0.0.1
license:        GPL
description:    Ralink Wireless Lan Linux Driver
author:         Ralink
srcversion:     357B7F974B7620617A6218F
alias:          usb:v0E8Dp7662d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp7632d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E8Dp2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp7612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v045Ep02E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17EBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p180Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9014d*dc*dsc*dp*ic*isc*ip*in*
depends:        cfg80211
retpoline:      Y
name:           mt7662u_sta
vermagic:       4.15.0-43-generic SMP mod_unload 
parm:           mac:rt_wifi: wireless mac addr (charp)
parm:           mode:rt_wifi: wireless operation mode (charp)

```

~$ iwconfig 
```

wlan0     Ralink STA  
          
enp1s0    no wireless extensions.


lo        no wireless extensions.


enp3s0    no wireless extensions.

```

~$ sudo hostapd -d hostapd.conf 
```

random: Trying to read entropy from /dev/random
Configuration file: hostapd.conf
nl80211: Supported cipher 00-0f-ac:1
nl80211: Supported cipher 00-0f-ac:5
nl80211: Supported cipher 00-0f-ac:2
nl80211: Supported cipher 00-0f-ac:4
nl80211: interface wlan0 in phy phy0
nl80211: Set mode ifindex 4 iftype 3 (AP)
nl80211: Setup AP(wlan0) - device_ap_sme=1 use_monitor=0
nl80211: Subscribe to mgmt frames with AP handle 0x557603665320 (device SME)
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x557603665320 match=04
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x557603665320 match=0501
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x557603665320 match=0504
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x557603665320 match=06
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x557603665320 match=08
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x557603665320 match=09
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x557603665320 match=0a
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x557603665320 match=11
nl80211: Register frame type=0xd0 (WLAN_FC_STYPE_ACTION) nl_handle=0x557603665320 match=7f
nl80211: Enable Probe Request reporting nl_preq=0x5576036688d0
nl80211: Register frame type=0x40 (WLAN_FC_STYPE_PROBE_REQ) nl_handle=0x5576036688d0 match=
rfkill: initial event: idx=0 type=1 op=0 soft=0 hard=0
nl80211: Add own interface ifindex 4 (ifidx_reason -1)
nl80211: if_indices[16]: 4(-1)
phy: phy0
BSS count 1, BSSID mask 00:00:00:00:00:00 (0 bits)
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
Completing interface initialization
Mode: IEEE 802.11g  Channel: 6  Frequency: 2437 MHz
DFS 0 channels required radar detection
nl80211: Set freq 2437 (ht_enabled=0, vht_enabled=0, bandwidth=20 MHz, cf1=2437 MHz, cf2=0 MHz)
  * freq=2437
  * vht_enabled=0
  * ht_enabled=0
  * channel_type=0
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
hostapd_setup_bss(hapd=0x5576036620f0 (wlan0), first=1)
wlan0: Flushing old station entries
nl80211: flush -> DEL_STATION wlan0 (all)
wlan0: Deauthenticate all stations
nl80211: sta_remove -> DEL_STATION wlan0 ff:ff:ff:ff:ff:ff --> 0 (Success)
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=0 addr=(nil) key_idx=3 set_tx=0 seq_len=0 key_len=0
Using interface wlan0 with hwaddr 40:a5:ef:4e:c9:23 and ssid "A1X2X3X4X"
Deriving WPA PSK based on passphrase
SSID - hexdump_ascii(len=9):
     41 31 58 32 58 33 58 34 58                        A1X2X3X4X       
PSK (ASCII passphrase) - hexdump_ascii(len=11): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
random: Got 15/20 bytes from /dev/random
random: Only 15/20 bytes of strong random data available from /dev/random
random: Not enough entropy pool available for secure operations
WPA: Not enough entropy in random pool for secure operations - update keys later when the first station connects
GMK - hexdump(len=32): [REMOVED]
Key Counter - hexdump(len=32): [REMOVED]
WPA: Delay group state machine start until Beacon frames have been configured
nl80211: Set beacon (beacon_set=0)
nl80211: Beacon head - hexdump(len=60): 80 00 00 00 ff ff ff ff ff ff 40 a5 ef 4e c9 23 40 a5 ef 4e c9 23 00 00 00 00 00 00 00 00 00 00 64 00 11 04 00 09 41 31 58 32 58 33 58 34 58 01 08 82 84 8b 96 0c 12 18 24 03 01 06
nl80211: Beacon tail - hexdump(len=61): 2a 01 04 32 04 30 48 60 6c 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 7f 04 00 00 00 02
nl80211: ifindex=4
nl80211: beacon_int=100
nl80211: dtim_period=2
nl80211: ssid - hexdump_ascii(len=9):
     41 31 58 32 58 33 58 34 58                        A1X2X3X4X       
  * beacon_int=100
  * dtim_period=2
nl80211: hidden SSID not in use
nl80211: privacy=1
nl80211: auth_algs=0x1
nl80211: wpa_version=0x3
nl80211: key_mgmt_suites=0x2
nl80211: pairwise_ciphers=0x18
nl80211: group_cipher=0x8
nl80211: beacon_ies - hexdump(len=6): 7f 04 00 00 00 02
nl80211: proberesp_ies - hexdump(len=6): 7f 04 00 00 00 02
nl80211: assocresp_ies - hexdump(len=6): 7f 04 00 00 00 02
nl80211: ap_max_inactivity=300
WPA: Start group state machine to set initial keys
WPA: group state machine entering state GTK_INIT (VLAN-ID 0)
GTK - hexdump(len=32): [REMOVED]
WPA: group state machine entering state SETKEYSDONE (VLAN-ID 0)
wpa_driver_nl80211_set_key: ifindex=4 (wlan0) alg=2 addr=0x55760307c279 key_idx=1 set_tx=1 seq_len=0 key_len=32
nl80211: KEY_DATA - hexdump(len=32): [REMOVED]
   broadcast key
nl80211: Set wlan0 operstate 0->1 (UP)
netlink: Operstate: ifindex=4 linkmode=-1 (no change), operstate=6 (IF_OPER_UP)
Failed to set TX queue parameters for queue 0.
Failed to set TX queue parameters for queue 1.
Failed to set TX queue parameters for queue 2.
Failed to set TX queue parameters for queue 3.
wlan0: interface state UNINITIALIZED->ENABLED
wlan0: AP-ENABLED 
wlan0: Setup of interface done.
ctrl_iface not configured!
random: Got 5/5 bytes from /dev/random
RTM_NEWLINK: ifi_index=4 ifname=wlan0 operstate=0 linkmode=0 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK: ifi_index=4 ifname=wlan0 wext ifi_family=0 ifi_flags=0x11042 ([RUNNING][LOWER_UP])
nl80211: Ignore interface down event since interface wlan0 is up
RTM_NEWLINK: ifi_index=4 ifname=wlan0 operstate=6 linkmode=0 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
VLAN: RTM_NEWLINK: ifi_index=4 ifname=wlan0 ifi_family=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
VLAN: vlan_newlink(wlan0)
^CSignal 2 received - terminating
hostapd_interface_deinit_free(0x557603660eb0)
hostapd_interface_deinit_free: num_bss=1 conf->num_bss=1
hostapd_interface_deinit(0x557603660eb0)
wlan0: interface state ENABLED->DISABLED
hostapd_bss_deinit: deinit bss wlan0
wlan0: Deauthenticate all stations
nl80211: sta_remove -> DEL_STATION wlan0 ff:ff:ff:ff:ff:ff --> 0 (Success)
wlan0: AP-DISABLED 
hostapd_cleanup(hapd=0x5576036620f0 (wlan0))
hostapd_free_hapd_data(wlan0)
hostapd_interface_deinit_free: driver=0x5576032debc0 drv_priv=0x557603663310 -> hapd_deinit
nl80211: deinit ifname=wlan0 disabled_11b_rates=0
nl80211: Disable Probe Request reporting nl_preq=0x8888ddfe8bee0059
nl80211: Remove monitor interface: refcount=0
nl80211: Remove beacon (ifindex=4)
netlink: Operstate: ifindex=4 linkmode=0 (kernel-control), operstate=6 (IF_OPER_UP)
nl80211: Set mode ifindex 4 iftype 2 (STATION)
nl80211: Teardown AP(wlan0) - device_ap_sme=1 use_monitor=0
nl80211: Unsubscribe mgmt frames handle 0x8888ddfe8beedba9 (AP teardown (dev SME))
hostapd_interface_free(0x557603660eb0)
hostapd_interface_free: free hapd 0x5576036620f0
hostapd_cleanup_iface(0x557603660eb0)
hostapd_cleanup_iface_partial(0x557603660eb0)
hostapd_cleanup_iface: free iface=0x557603660eb0

```

~$ cat hostapd.conf 
```

interface=wlan0
driver=nl80211
ssid=A1X2X3X4X
hw_mode=g
channel=6
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=my_password
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

```

---

### Post by praseodym on 2019-01-27
"wlan0" is the right interface name?

Show "ifconfig -a"

---

### Post by rekikn12 on 2019-01-27
~$ ifconfig -a
```

enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536


wlan0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether 00:00:00:00:00:00  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

### Post by rekikn12 on 2019-01-28
I make another advance. 
If run a **~$ iwlist wlan0 scan** before **~$ sudo hostapd -d hostapd.conf** , the AP is created and i can see the AP in anothers devices. But, i can't connect yet.

that is the output when i try to connect to AP 
~$ sudo hostapd -d hostapd.conf 
```

nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=c8:e0:eb:3d:1e:37 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0x8d00 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=108
nl80211: send_mlme - da= c8:e0:eb:3d:1e:37 noack=0 freq=0 no_cck=0 offchanok=0 wait_time=0 fc=0x50 (WLAN_FC_STYPE_PROBE_RESP) nlmode=3
nl80211: Use bss->freq=2437
nl80211: Drop oldest pending send action cookie 0x0
nl80211: Drv Event 60 (NL80211_CMD_FRAME_TX_STATUS) received for wlan0
nl80211: Frame TX status event
wlan0: Event TX_STATUS (17) received
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=c8:e0:eb:3d:1e:37 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0x8d10 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=108
nl80211: send_mlme - da= c8:e0:eb:3d:1e:37 noack=0 freq=0 no_cck=0 offchanok=0 wait_time=0 fc=0x50 (WLAN_FC_STYPE_PROBE_RESP) nlmode=3
nl80211: Use bss->freq=2437
nl80211: Drop oldest pending send action cookie 0x0
nl80211: Drv Event 60 (NL80211_CMD_FRAME_TX_STATUS) received for wlan0
nl80211: Frame TX status event
wlan0: Event TX_STATUS (17) received
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=c8:e0:eb:3d:1e:37 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0x8d60 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=108
Ignore Probe Request due to DS Params mismatch: chan=6 != ds.chan=5
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=c8:e0:eb:3d:1e:37 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0x8d90 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=108
Ignore Probe Request due to DS Params mismatch: chan=6 != ds.chan=7
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=00:57:c1:da:88:00 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0xdc70 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=68
nl80211: send_mlme - da= 00:57:c1:da:88:00 noack=1 freq=0 no_cck=0 offchanok=0 wait_time=0 fc=0x50 (WLAN_FC_STYPE_PROBE_RESP) nlmode=3
nl80211: Use bss->freq=2437
nl80211: Drop oldest pending send action cookie 0x0
nl80211: Drv Event 60 (NL80211_CMD_FRAME_TX_STATUS) received for wlan0
nl80211: Frame TX status event
wlan0: Event TX_STATUS (17) received
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=00:57:c1:da:88:00 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0xdc80 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=68
nl80211: send_mlme - da= 00:57:c1:da:88:00 noack=1 freq=0 no_cck=0 offchanok=0 wait_time=0 fc=0x50 (WLAN_FC_STYPE_PROBE_RESP) nlmode=3
nl80211: Use bss->freq=2437
nl80211: Drop oldest pending send action cookie 0x0
nl80211: Drv Event 60 (NL80211_CMD_FRAME_TX_STATUS) received for wlan0
nl80211: Frame TX status event
wlan0: Event TX_STATUS (17) received
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=0c:91:60:f8:85:d4 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0x260 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=221
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=0c:91:60:f8:85:d4 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0x270 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=217
nl80211: send_mlme - da= 0c:91:60:f8:85:d4 noack=1 freq=0 no_cck=0 offchanok=0 wait_time=0 fc=0x50 (WLAN_FC_STYPE_PROBE_RESP) nlmode=3
nl80211: Use bss->freq=2437
nl80211: Drop oldest pending send action cookie 0x0
nl80211: Drv Event 60 (NL80211_CMD_FRAME_TX_STATUS) received for wlan0
nl80211: Frame TX status event
wlan0: Event TX_STATUS (17) received
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=c8:e0:eb:3d:1e:37 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0x8fe0 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=108
nl80211: send_mlme - da= c8:e0:eb:3d:1e:37 noack=0 freq=0 no_cck=0 offchanok=0 wait_time=0 fc=0x50 (WLAN_FC_STYPE_PROBE_RESP) nlmode=3
nl80211: Use bss->freq=2437
nl80211: Drop oldest pending send action cookie 0x0
nl80211: Drv Event 60 (NL80211_CMD_FRAME_TX_STATUS) received for wlan0
nl80211: Frame TX status event
wlan0: Event TX_STATUS (17) received
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=c8:e0:eb:3d:1e:37 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0x8ff0 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=108
nl80211: send_mlme - da= c8:e0:eb:3d:1e:37 noack=0 freq=0 no_cck=0 offchanok=0 wait_time=0 fc=0x50 (WLAN_FC_STYPE_PROBE_RESP) nlmode=3
nl80211: Use bss->freq=2437
nl80211: Drop oldest pending send action cookie 0x0
nl80211: Drv Event 60 (NL80211_CMD_FRAME_TX_STATUS) received for wlan0
nl80211: Frame TX status event
wlan0: Event TX_STATUS (17) received
nl80211: BSS Event 59 (NL80211_CMD_FRAME) received for wlan0
nl80211: RX frame da=ff:ff:ff:ff:ff:ff sa=c8:e0:eb:3d:1e:37 bssid=ff:ff:ff:ff:ff:ff freq=2437 ssi_signal=0 fc=0x40 seq_ctrl=0x9070 stype=4 (WLAN_FC_STYPE_PROBE_REQ) len=108
Ignore Probe Request due to DS Params mismatch: chan=6 != ds.chan=7

```

---

### Post by praseodym on 2019-01-29
bssid=ff:ff:ff:ff:ff:ff

I don't belive this is the MAC address of your AP, is it?

---

