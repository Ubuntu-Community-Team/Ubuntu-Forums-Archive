---
title: "Gnome shell crashes when restarting networking daemon."
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by James_Ridey on 2013-10-22
Hello,
When I restart networking on my ThinkPad X130e the DE crashes, followed by X completely halting.
I restarted networking using ```
service networking restart
```. This *may* be linked to another issue with my Linux install, where my networking stack doesn't work after hibernation.


The relevant output of ```
dmesg
``` is:
```
-- snip --
[10218.408501] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[10218.408516] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[10218.409757] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10238.068627] init: systemd-logind main process (1203) killed by TERM signal
[10238.482930] init: cups-browsed main process ended, respawning
[10238.532575] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[10239.995671] init: Disconnected from system bus
[10241.915276] init: whoopsie main process ended, respawning
[10244.011360] init: modemmanager main process (1250) killed by KILL signal
[10249.215830] wallch[2657]: segfault at 7f6a04540b68 ip 00007f6a0e8153ed sp 00007fff990ec228 error 4 in libQt5Core.so.5.0.2[7f6a0e5e1000+407000]

```


Also in my .xsessions-errors is
```
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: upstart-dbus-session-bridge main process (1571) terminated with status 1
init: hud main process (1592) killed by TERM signal
init: gnome-settings-daemon main process (1589) terminated with status 1
init: gnome-session main process (1596) killed by TERM signal





```


My Gnome-Shell version is 3.10.0.1, my Ubuntu version is 13.10. This error has persisted through several versions of Gnome Shell 3.x and Ubuntu versions. This leads me to believe the error is more deep-seated than the a bug in Gnome.


The output of ```
iw list
``` is:
```

Wiphy phy0
	Band 1:
		Capabilities: 0x70
			HT20
			Static SM Power Save
			RX Greenfield
			RX HT20 SGI
			RX HT40 SGI
			No RX STBC
			Max AMSDU length: 3839 bytes
			No DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 8 usec (0x06)
		HT TX/RX MCS rate indexes supported: 0-15
		Frequencies:
			* 2412 MHz [1] (19.0 dBm)
			* 2417 MHz [2] (19.0 dBm)
			* 2422 MHz [3] (19.0 dBm)
			* 2427 MHz [4] (19.0 dBm)
			* 2432 MHz [5] (19.0 dBm)
			* 2437 MHz [6] (19.0 dBm)
			* 2442 MHz [7] (19.0 dBm)
			* 2447 MHz [8] (19.0 dBm)
			* 2452 MHz [9] (19.0 dBm)
			* 2457 MHz [10] (19.0 dBm)
			* 2462 MHz [11] (19.0 dBm)
			* 2467 MHz [12] (19.0 dBm) (passive scanning, no IBSS)
			* 2472 MHz [13] (19.0 dBm) (passive scanning, no IBSS)
			* 2484 MHz [14] (disabled)
		Bitrates (non-HT):
			* 1.0 Mbps
			* 2.0 Mbps (short preamble supported)
			* 5.5 Mbps (short preamble supported)
			* 11.0 Mbps (short preamble supported)
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
	Band 2:
		Capabilities: 0x70
			HT20
			Static SM Power Save
			RX Greenfield
			RX HT20 SGI
			RX HT40 SGI
			No RX STBC
			Max AMSDU length: 3839 bytes
			No DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 8 usec (0x06)
		HT TX/RX MCS rate indexes supported: 0-15
		Frequencies:
			* 5180 MHz [36] (21.0 dBm)
			* 5200 MHz [40] (21.0 dBm) (passive scanning, no IBSS)
			* 5220 MHz [44] (21.0 dBm) (passive scanning, no IBSS)
			* 5240 MHz [48] (21.0 dBm)
			* 5260 MHz [52] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5280 MHz [56] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5300 MHz [60] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5320 MHz [64] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5500 MHz [100] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5520 MHz [104] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5540 MHz [108] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5560 MHz [112] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5580 MHz [116] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5600 MHz [120] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5620 MHz [124] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5640 MHz [128] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5660 MHz [132] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5680 MHz [136] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5700 MHz [140] (21.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5745 MHz [149] (21.0 dBm)
			* 5765 MHz [153] (21.0 dBm) (passive scanning, no IBSS)
			* 5785 MHz [157] (21.0 dBm)
			* 5805 MHz [161] (21.0 dBm) (passive scanning, no IBSS)
			* 5825 MHz [165] (21.0 dBm) (passive scanning, no IBSS)
		Bitrates (non-HT):
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
	max # scan SSIDs: 4
	max scan IEs length: 2257 bytes
	Coverage class: 0 (up to 0m)
	Supported Ciphers:
		* WEP40 (00-0f-ac:1)
		* WEP104 (00-0f-ac:5)
		* TKIP (00-0f-ac:2)
		* CCMP (00-0f-ac:4)
	Available Antennas: TX 0 RX 0
	Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * monitor
	software interface modes (can always be added):
		 * AP/VLAN
		 * monitor
	interface combinations are not supported
	Supported commands:
		 * new_interface
		 * set_interface
		 * new_key
		 * new_beacon
		 * new_station
		 * new_mpath
		 * set_mesh_params
		 * set_bss
		 * authenticate
		 * associate
		 * deauthenticate
		 * disassociate
		 * join_ibss
		 * join_mesh
		 * set_tx_bitrate_mask
		 * action
		 * frame_wait_cancel
		 * set_wiphy_netns
		 * set_channel
		 * set_wds_peer
		 * Unknown command (84)
		 * Unknown command (87)
		 * Unknown command (85)
		 * Unknown command (89)
		 * Unknown command (92)
		 * testmode
		 * connect
		 * disconnect
	Supported TX frame types:
		 * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * mesh point: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * Unknown mode (10): 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
	Supported RX frame types:
		 * IBSS: 0x40 0xb0 0xc0 0xd0
		 * managed: 0x40 0xd0
		 * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * mesh point: 0xb0 0xc0 0xd0
		 * P2P-client: 0x40 0xd0
		 * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * Unknown mode (10): 0x40 0xd0
	Device supports RSN-IBSS.
	HT Capability overrides:
		 * MCS: ff ff ff ff ff ff ff ff ff ff
		 * maximum A-MSDU length
		 * supported channel width
		 * short GI for 40 MHz
		 * max A-MPDU length exponent
		 * min MPDU start spacing
	Device supports TX status socket option.
	Device supports HT-IBSS.

```

---

### Post by phDaemon on 2013-11-05
Same thing here. Ubuntu 13.04 gnome-shell 3.8.3

---

