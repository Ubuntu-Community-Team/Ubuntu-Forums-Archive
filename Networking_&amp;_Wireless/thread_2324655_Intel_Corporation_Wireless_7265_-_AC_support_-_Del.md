---
title: "Intel Corporation Wireless 7265 - AC support - Dell latitude E7450"
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by blackgr on 2016-05-15
Hello,

I hope you are all well.
I have a dell latitude E7450 with the following wifi card: "Intel Corporation Wireless 7265".
Although this is an AC card, iwconfig reports "IEEE 802.11abgn".
I don't currently have an AC router. Is there a way to check if the linux drivers are AC ready?
Same behavior under 16.04.

```
$ lspci -nn | grep -i wireless
02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)

```


```
$ lsb_release -d
Description:	Ubuntu 15.10
```

```
$ iwconfig wlan0 
wlan0     IEEE 802.11abgn  ESSID:"******"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: ****** 
          Bit Rate=1 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:135   Missed beacon:0
```

```
$ dmesg  | grep iwlwifi
[    2.600316] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    2.605934] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-15.ucode failed with error -2
[    2.605966] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-14.ucode failed with error -2
[    2.621500] iwlwifi 0000:02:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    2.686882] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    2.687386] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    2.687991] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.579869] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.580478] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.643795] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.644345] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
```


```
$ python ucode.py /lib/firmware/*7265D*.ucode
/lib/firmware/iwlwifi-7265D-10.ucode : ver 23.15.10.0 (stream:CoreCycle7_stab@128913)
/lib/firmware/iwlwifi-7265D-12.ucode : ver 25.17.12.0 (stream:CoreCycle9_stab_linux@145607)
/lib/firmware/iwlwifi-7265D-13.ucode : ver 25.30.13.0 (stream:CoreCycle10_stab@183742)
```

```
$ iw list
Wiphy phy0
	max # scan SSIDs: 20
	max scan IEs length: 425 bytes
	Retry short limit: 7
	Retry long limit: 4
	Coverage class: 0 (up to 0m)
	Device supports RSN-IBSS.
	Device supports AP-side u-APSD.
	Device supports T-DLS.
	Supported Ciphers:
		* WEP40 (00-0f-ac:1)
		* WEP104 (00-0f-ac:5)
		* TKIP (00-0f-ac:2)
		* CCMP (00-0f-ac:4)
		* CMAC (00-0f-ac:6)
	Available Antennas: TX 0 RX 0
	Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * monitor
		 * P2P-client
		 * P2P-GO
		 * P2P-device
	Band 1:
		Capabilities: 0x11e3
			RX LDPC
			HT20/HT40
			Static SM Power Save
			RX HT20 SGI
			RX HT40 SGI
			TX STBC
			RX STBC 1-stream
			Max AMSDU length: 3839 bytes
			DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 4 usec (0x05)
		HT TX/RX MCS rate indexes supported: 0-15
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
		Frequencies:
			* 2412 MHz [1] (22.0 dBm)
			* 2417 MHz [2] (22.0 dBm)
			* 2422 MHz [3] (22.0 dBm)
			* 2427 MHz [4] (22.0 dBm)
			* 2432 MHz [5] (22.0 dBm)
			* 2437 MHz [6] (22.0 dBm)
			* 2442 MHz [7] (22.0 dBm)
			* 2447 MHz [8] (22.0 dBm)
			* 2452 MHz [9] (22.0 dBm)
			* 2457 MHz [10] (22.0 dBm)
			* 2462 MHz [11] (22.0 dBm)
			* 2467 MHz [12] (22.0 dBm) (no IR)
			* 2472 MHz [13] (22.0 dBm) (no IR)
			* 2484 MHz [14] (disabled)
	Band 2:
		Capabilities: 0x11e3
			RX LDPC
			HT20/HT40
			Static SM Power Save
			RX HT20 SGI
			RX HT40 SGI
			TX STBC
			RX STBC 1-stream
			Max AMSDU length: 3839 bytes
			DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 4 usec (0x05)
		HT TX/RX MCS rate indexes supported: 0-15
		VHT Capabilities (0x038071b0):
			Max MPDU length: 3895
			Supported Channel Width: neither 160 nor 80+80
			RX LDPC
			short GI (80 MHz)
			TX STBC
			SU Beamformee
		VHT RX MCS set:
			1 streams: MCS 0-9
			2 streams: MCS 0-9
			3 streams: not supported
			4 streams: not supported
			5 streams: not supported
			6 streams: not supported
			7 streams: not supported
			8 streams: not supported
		VHT RX highest supported: 0 Mbps
		VHT TX MCS set:
			1 streams: MCS 0-9
			2 streams: MCS 0-9
			3 streams: not supported
			4 streams: not supported
			5 streams: not supported
			6 streams: not supported
			7 streams: not supported
			8 streams: not supported
		VHT TX highest supported: 0 Mbps
		Bitrates (non-HT):
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
		Frequencies:
			* 5180 MHz [36] (22.0 dBm) (no IR)
			* 5200 MHz [40] (22.0 dBm) (no IR)
			* 5220 MHz [44] (22.0 dBm) (no IR)
			* 5240 MHz [48] (22.0 dBm) (no IR)
			* 5260 MHz [52] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5280 MHz [56] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5300 MHz [60] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5320 MHz [64] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5500 MHz [100] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5520 MHz [104] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5540 MHz [108] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5560 MHz [112] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5580 MHz [116] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5600 MHz [120] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5620 MHz [124] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5640 MHz [128] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5660 MHz [132] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5680 MHz [136] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5700 MHz [140] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5720 MHz [144] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 1805 sec)
			  DFS CAC time: 60000 ms
			* 5745 MHz [149] (22.0 dBm) (no IR)
			* 5765 MHz [153] (22.0 dBm) (no IR)
			* 5785 MHz [157] (22.0 dBm) (no IR)
			* 5805 MHz [161] (22.0 dBm) (no IR)
			* 5825 MHz [165] (22.0 dBm) (no IR)
	Supported commands:
		 * new_interface
		 * set_interface
		 * new_key
		 * start_ap
		 * new_station
		 * new_mpath
		 * set_mesh_config
		 * set_bss
		 * authenticate
		 * associate
		 * deauthenticate
		 * disassociate
		 * join_ibss
		 * join_mesh
		 * remain_on_channel
		 * set_tx_bitrate_mask
		 * frame
		 * frame_wait_cancel
		 * set_wiphy_netns
		 * set_channel
		 * set_wds_peer
		 * tdls_mgmt
		 * tdls_oper
		 * start_sched_scan
		 * probe_client
		 * set_noack_map
		 * register_beacons
		 * start_p2p_device
		 * set_mcast_rate
		 * channel_switch
		 * Unknown command (104)
		 * Unknown command (105)
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
		 * P2P-device: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
	Supported RX frame types:
		 * IBSS: 0x40 0xb0 0xc0 0xd0
		 * managed: 0x40 0xd0
		 * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * mesh point: 0xb0 0xc0 0xd0
		 * P2P-client: 0x40 0xd0
		 * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * P2P-device: 0x40 0xd0
	WoWLAN support:
		 * wake up on disconnect
		 * wake up on magic packet
		 * wake up on pattern match, up to 20 patterns of 16-128 bytes,
		   maximum packet offset 0 bytes
		 * can do GTK rekeying
		 * wake up on GTK rekey failure
		 * wake up on EAP identity request
		 * wake up on 4-way handshake
		 * wake up on rfkill release
		 * wake up on TCP connection
	software interface modes (can always be added):
		 * AP/VLAN
		 * monitor
	valid interface combinations:
		 * #{ managed } <= 1, #{ AP, P2P-client, P2P-GO } <= 1, #{ P2P-device } <= 1,
		   total <= 3, #channels <= 2
	HT Capability overrides:
		 * MCS: ff ff ff ff ff ff ff ff ff ff
		 * maximum A-MSDU length
		 * supported channel width
		 * short GI for 40 MHz
		 * max A-MPDU length exponent
		 * min MPDU start spacing
	Device supports TX status socket option.
	Device supports HT-IBSS.
	Device supports SAE with AUTHENTICATE command
	Device supports low priority scan.
	Device supports scan flush.
	Device supports per-vif TX power setting
	P2P GO supports CT window setting
	P2P GO supports opportunistic powersave setting
	Driver supports a userspace MPM
	Device supports static SMPS
	Device supports dynamic SMPS

```
Thanks,
Alex

---

### Post by blackgr on 2016-05-15
After checking around, it seems that since the "iw list" output returns "VHT" entries, it does support AC.

---

