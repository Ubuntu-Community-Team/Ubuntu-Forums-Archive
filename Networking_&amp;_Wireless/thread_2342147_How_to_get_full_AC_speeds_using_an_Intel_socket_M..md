---
title: "How to get full AC speeds using an Intel socket M.2 card on my laptop."
date: 2016-11-04
forum: Networking &amp; Wireless
---

### Post by cdysthe on 2016-11-04
My laptop came with a Broadcom Wi-Fi card with the M.2 socket. I got great AC speed with the card on my network, up over 800 Mb/s at times but the connections dropped randomly including wired connections. So I purchased an Intel 7265NGW card which was recognized and works just fine. The connections are rock solid, but I am only getting N speeds which means it tops out at 300 Mb/s. I do want to stick to Intel since it always works, but how can I get AC speed with this card, and if I can't what would I have to get to get the same performance as the Broadcom card offered? I mostly connect to Netgear Nighthawk and Ubiquity access points. I am running Ubuntu 16.10 with the 4.8.0-27-generic #29-Ubuntu SMP kernel.

---

### Post by chili555 on 2016-11-05
The ability to hit AC speeds is very much dependent on three things; the card, the driver (and associated firmware) and the router.

First, I assume, since you are running 16.10, that you have the latest firmware; check:```
dmesg | grep iwl
```Next, let's see what the card capabilities are:```
iw list
```We are interested in the lines corresponding to these from my machine:```
VHT Capabilities (0x038071a0):
			Max MPDU length: 3895
			[COLOR="#FF0000"]Supported Channel Width: neither 160 nor 80+80[/COLOR]
			short GI (80 MHz)
			TX STBC
			SU Beamformee
		VHT RX MCS set:
			[COLOR="#FF0000"]1 streams: MCS 0-9
			2 streams: MCS 0-9[/COLOR]
			3 streams: not supported
			4 streams: not supported
			5 streams: not supported
			6 streams: not supported
			7 streams: not supported
			8 streams: not supported

```As you can see, my card, driver and firmware combination are incapable of 160 and 80+80 channels width. With 2 streams and MCS 9, I will therefore be limited to about 400 Mb/s. A recent speed test shows that I got 368/325.

[https://en.wikipedia.org/wiki/IEEE_802.11ac](https://en.wikipedia.org/wiki/IEEE_802.11ac)

Next, I'd look at the settings in the router. I assume, since the Broadcom did 800 Mb/s, that the router is set up correctly, however.

Let's see what your card reports and go from there.

---

### Post by cdysthe on 2016-11-08
Hi,

Here's the output of dmesg | grep iwl:

```
[    3.685598] iwlwifi 0000:01:00.0: Unsupported splx structure
[    3.686696] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[    3.686724] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[    3.691264] iwlwifi 0000:01:00.0: loaded firmware version 22.361476.0 op_mode iwlmvm
[    3.743012] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    3.745334] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    3.745783] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    3.831455] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.920273] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    5.917413] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    5.917917] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    5.986538] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    5.987036] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled

```

Here's the output from 'iw list'. I could not find the exact data you show from yours, so I included it all:

```
Wiphy phy0
	max # scan SSIDs: 20
	max scan IEs length: 439 bytes
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
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5280 MHz [56] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5300 MHz [60] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5320 MHz [64] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5500 MHz [100] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5520 MHz [104] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5540 MHz [108] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5560 MHz [112] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5580 MHz [116] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5600 MHz [120] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5620 MHz [124] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5640 MHz [128] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5660 MHz [132] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5680 MHz [136] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5700 MHz [140] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
			  DFS CAC time: 60000 ms
			* 5720 MHz [144] (22.0 dBm) (no IR, radar detection)
			  DFS state: usable (for 4104 sec)
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
	Driver supports full state transitions for AP/GO clients
	Driver supports a userspace MPM
	Driver/device bandwidth changes during BSS lifetime (AP/GO mode)
	Device supports static SMPS
	Device supports dynamic SMPS

```

My router which is a Netgear Nighthawk R7000 with an EX7000 extender on the second floor. Both run the latest firmware with close to default settings for wireless. At work there's Since I get much higher speed  with the Broadcom card I would assume things are okay on the router side. At works I connect to an Ubiquiti system but I'm not getting over the 300 Mb/s there either. If there are certain settings in my router I should be aware of to get this Intel card to perform please let me know.

I hope this information will help you determine if this is all I can expect from this card. If it is it would be great with a recommendation for another Wi-Fi card I could get. I do not want to go back to the Broadcom since it's very unstable and I have to reboot several times a day and restart networking several times an hour.

---

### Post by chili555 on 2016-11-08
Wow! You do have very different readings than my (it would seem) similar Intel 7260.

I see two things that may be useful:> [    3.686696] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-[COLOR="#FF0000"]24[/COLOR].ucode failed with error -2
[    3.686724] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-7265D-[COLOR="#FF0000"]23[/COLOR].ucode failed with error -2
[    3.691264] iwlwifi 0000:01:00.0: loaded firmware version [COLOR="#FF0000"]22[/COLOR].361476.0 op_mode iwlmvmThe driver would like -24 but didn't find it; likewise -23 and then found and used -22.

This page suggests that -23 and -24 are not ready for prime-time: [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release)

However, this page says it has the files! [https://github.com/NetBit73/NeteXt73_pakiety/tree/master/iwlwifi](https://github.com/NetBit73/NeteXt73_pakiety/tree/master/iwlwifi) I doubt that we have much to lose to download and try them:```
cd /lib/firmware
sudo wget https://github.com/NetBit73/NeteXt73_pakiety/raw/master/iwlwifi/iwlwifi-7265D-23.ucode
sudo wget https://github.com/NetBit73/NeteXt73_pakiety/raw/master/iwlwifi/iwlwifi-7265D-24.ucode
```Reboot. See what firmware loaded:```
dmesg | grep iwl
```Evaluate. Is the speed better or worse? If it is worse, remove -24 and reboot and re-evaluate:```
sudo rm /lib/firmware/iwlwifi-7265D-24.ucode
```Likewise with -23.

Next, we see:> Band 1:
		Capabilities: 0x11e3
			RX LDPC
			[COLOR="#FF0000"]HT20/HT40[/COLOR]
			Static SM Power Save
			RX HT20 SGI
			RX HT40 SGI
			TX STBC
			RX STBC 1-stream
			Max AMSDU length: 3839 bytes
			DSSS/CCK HT40This page suggests that the channel selection is part of whether you can use the 20 MHz channel width or 40 or 80, etc. More is better! [http://www.revolutionwifi.net/revolutionwifi/2013/03/80211ac-channel-planning.html](http://www.revolutionwifi.net/revolutionwifi/2013/03/80211ac-channel-planning.html)

Obviously, then, set your router to either auto channel selection or, in your case, since the card does 40 Mhz, evidently, a fixed channel of 38, 46, 54, 62, 102, 110, 118, 126, 134, 142, 151 or 159. 

Again, since the Broadcom did 800 MHz, I assume the router is set correctly, but check.

As for what card reliably does AC in Ubuntu, I have no suggestions. I am learning more every day.

---

### Post by cdysthe on 2016-11-10
Hi,

I downloaded the firmware you found. I get the same exact 300 Mb/s and the following output:

```
user@puter:~$ dmesg | grep iwl
[    3.683035] iwlwifi 0000:01:00.0: loaded firmware version 22.361476.0 op_mode iwlmvm
[    3.683075] iwlwifi 0000:01:00.0: Unsupported splx structure
[    3.729150] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    3.731474] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    3.731925] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    3.811897] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.902239] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    5.797548] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    5.798001] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    5.863727] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    5.864178] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled

```

Looks like the error messages are gone from the output but the maximum speed is the same. 

There's not much to change on the Netgear Nighthawk R7000 annd even less on the  Netgear Nighthawk EX7000 extender. The speed is the same regardless of whether I connect to the router itself or the extender. 300 Mb/s always. The channel set is 149 and there's no auto setting for the 5ghz and not other settings either. These two are on: "Implicit BEAMFORMING - Boosts WiFi speed, reliability, & range for all mobile device and "Enable AIRTIME FAIRNESS - Prevent network lag when slower devices connect". But the Broadcom card is consitently getting up to around 800 Mp/s so I do not thing it's the router/extender which both are of relatively good quality.

---

### Post by chili555 on 2016-11-10
> The channel set is 149Is 151 or 159 available as I suggested? 

I am wondering why the now available -23 and -24 firmware files were not loaded.

---

### Post by cdysthe on 2016-11-10
Hi,

I only have channels 149, 153, 157 and 161 available so only 149 were a match. As for the firmware being loaded, you would know much better than I do. This firmware problem is based on that the card is too new or two old? Thank you so much for trying to help. If this doesn't work out could you suggest a card you think would work? They are not very expensive these days anyway.

---

### Post by chili555 on 2016-11-10
> **cdysthe said:**
> Hi,

I only have channels 149, 153, 157 and 161 available so only 149 were a match. As for the firmware being loaded, you would know much better than I do. This firmware problem is based on that the card is too new or two old? Thank you so much for trying to help. If this doesn't work out could you suggest a card you think would work? They are not very expensive these days anyway.As for what card reliably does AC in Ubuntu, I have no suggestions. I am learning more every day.

Care to attempt to troubleshoot the Broadcom?

---

### Post by jeremy31 on 2016-11-11
I wonder if the Intel card needs a parameter setting changed from default
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlopt.conf
```

Reboot

---

### Post by cdysthe on 2016-11-14
Hi,

The Broadcom has been so problematic and unstable I do not think I will be able to get it working right. I see many others have problems with it also. I would rather keep the slower card than having these random problems. It does look like AC support isn't present for Linux for this card yet. I wonder if that means I could just wait and hope it gets there eventually. Thoughts on that?

---

### Post by chili555 on 2016-11-15
I think AC is present depending on a great many factors and, as a result, is very difficult to actually achieve. I also think the Intel driver and firmware continue to be developed and pushed out. That's a round-about way of saying; yes, wait and see.

---

