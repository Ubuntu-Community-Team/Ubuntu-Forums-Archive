---
title: "rtl8812ae no 5Ghz"
date: 2017-06-25
forum: Networking &amp; Wireless
---

### Post by Forbees on 2017-06-25
ubuntu 17.04
started off as connection drops and slow speeds, a few hours of searching and i've disabled wireless N on my router for 2.4Ghz,  installed the rtl8821ae driver, removed the default network manager and installed Wicd, which seems to get the 2.4Ghz wireless G speeds between 200KB/s and 1.4MB/s and connection stable


but it seems no matter what i try i can't connect to the 5Ghz band to get wireless N or AC. the card supports it, didn't have problems on windows (cringe), but when trying to connect it times out during authentication and claims bad password

every thread i find with people asking about this chip and 5Ghz seems to be unresolved, but also dating as far back at 2014. you'd think in 3 years someone would have figured this out?

here's some dumps of info

```

 lspci | grep Wireless
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter (rev 01)

```
```
 sudo lshw -c network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 09
       serial: bc:ee:7b:e1:64:d7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.5 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:39 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: RTL8812AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlp5s0
       version: 01
       serial: 96:10:b7:4a:f4:fe
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.10.0-24-generic firmware=N/A ip=192.168.1.140 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:43 ioport:c000(size=256) memory:fc300000-fc303fff

```
```
 iw list
Wiphy phy0
	max # scan SSIDs: 4
	max scan IEs length: 2243 bytes
	max # sched scan SSIDs: 0
	max # match sets: 0
	max # scan plans: 1
	max scan plan interval: -1
	max scan plan iterations: 0
	RTS threshold: 2347
	Retry short limit: 7
	Retry long limit: 4
	Coverage class: 0 (up to 0m)
	Device supports RSN-IBSS.
	Supported Ciphers:
		* WEP40 (00-0f-ac:1)
		* WEP104 (00-0f-ac:5)
		* TKIP (00-0f-ac:2)
		* CCMP-128 (00-0f-ac:4)
		* CCMP-256 (00-0f-ac:10)
		* GCMP-128 (00-0f-ac:8)
		* GCMP-256 (00-0f-ac:9)
		* CMAC (00-0f-ac:6)
		* CMAC-256 (00-0f-ac:13)
		* GMAC-128 (00-0f-ac:11)
		* GMAC-256 (00-0f-ac:12)
	Available Antennas: TX 0 RX 0
	Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * monitor
		 * mesh point
		 * P2P-client
		 * P2P-GO
	Band 1:
		Capabilities: 0x186e
			HT20/HT40
			SM Power Save disabled
			RX HT20 SGI
			RX HT40 SGI
			No RX STBC
			Max AMSDU length: 7935 bytes
			DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 16 usec (0x07)
		HT Max RX data rate: 300 Mbps
		HT TX/RX MCS rate indexes supported: 0-15, 32
		Bitrates (non-HT):
			* 1.0 Mbps
			* 2.0 Mbps
			* 5.5 Mbps
			* 11.0 Mbps
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
		Frequencies:
			* 2412 MHz [1] (20.0 dBm)
			* 2417 MHz [2] (20.0 dBm)
			* 2422 MHz [3] (20.0 dBm)
			* 2427 MHz [4] (20.0 dBm)
			* 2432 MHz [5] (20.0 dBm)
			* 2437 MHz [6] (20.0 dBm)
			* 2442 MHz [7] (20.0 dBm)
			* 2447 MHz [8] (20.0 dBm)
			* 2452 MHz [9] (20.0 dBm)
			* 2457 MHz [10] (20.0 dBm)
			* 2462 MHz [11] (20.0 dBm)
			* 2467 MHz [12] (20.0 dBm)
			* 2472 MHz [13] (20.0 dBm)
			* 2484 MHz [14] (disabled)
	Band 2:
		Capabilities: 0x186e
			HT20/HT40
			SM Power Save disabled
			RX HT20 SGI
			RX HT40 SGI
			No RX STBC
			Max AMSDU length: 7935 bytes
			DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 16 usec (0x07)
		HT Max RX data rate: 300 Mbps
		HT TX/RX MCS rate indexes supported: 0-15, 32
		VHT Capabilities (0x33c019a3):
			Max MPDU length: (reserved)
			Supported Channel Width: neither 160 nor 80+80
			short GI (80 MHz)
			TX STBC
			SU Beamformer
			SU Beamformee
			+HTC-VHT
			RX antenna pattern consistency
			TX antenna pattern consistency
		VHT RX MCS set:
			1 streams: MCS 0-9
			2 streams: MCS 0-9
			3 streams: not supported
			4 streams: not supported
			5 streams: not supported
			6 streams: not supported
			7 streams: not supported
			8 streams: not supported
		VHT RX highest supported: 867 Mbps
		VHT TX MCS set:
			1 streams: MCS 0-9
			2 streams: MCS 0-9
			3 streams: not supported
			4 streams: not supported
			5 streams: not supported
			6 streams: not supported
			7 streams: not supported
			8 streams: not supported
		VHT TX highest supported: 867 Mbps
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
			* 5180 MHz [36] (30.0 dBm)
			* 5200 MHz [40] (30.0 dBm)
			* 5220 MHz [44] (30.0 dBm)
			* 5240 MHz [48] (30.0 dBm)
			* 5260 MHz [52] (30.0 dBm) (no IR, radar detection)
			* 5280 MHz [56] (30.0 dBm) (no IR, radar detection)
			* 5300 MHz [60] (30.0 dBm) (no IR, radar detection)
			* 5320 MHz [64] (30.0 dBm) (no IR, radar detection)
			* 5500 MHz [100] (30.0 dBm) (no IR, radar detection)
			* 5520 MHz [104] (30.0 dBm) (no IR, radar detection)
			* 5540 MHz [108] (30.0 dBm) (no IR, radar detection)
			* 5560 MHz [112] (30.0 dBm) (no IR, radar detection)
			* 5580 MHz [116] (30.0 dBm) (no IR, radar detection)
			* 5600 MHz [120] (30.0 dBm) (no IR, radar detection)
			* 5620 MHz [124] (30.0 dBm) (no IR, radar detection)
			* 5640 MHz [128] (30.0 dBm) (no IR, radar detection)
			* 5660 MHz [132] (30.0 dBm) (no IR, radar detection)
			* 5680 MHz [136] (30.0 dBm) (no IR, radar detection)
			* 5700 MHz [140] (30.0 dBm) (no IR, radar detection)
			* 5745 MHz [149] (30.0 dBm)
			* 5765 MHz [153] (30.0 dBm)
			* 5785 MHz [157] (30.0 dBm)
			* 5805 MHz [161] (30.0 dBm)
			* 5825 MHz [165] (30.0 dBm)
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
		 * probe_client
		 * set_noack_map
		 * register_beacons
		 * start_p2p_device
		 * set_mcast_rate
		 * connect
		 * disconnect
		 * set_qos_map
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
		 * wake up on magic packet
		 * wake up on pattern match, up to 16 patterns of 13-128 bytes,
		   maximum packet offset 0 bytes
	software interface modes (can always be added):
		 * AP/VLAN
		 * monitor
	interface combinations are not supported
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
	Device supports AP scan.
	Device supports per-vif TX power setting
	Driver supports full state transitions for AP/GO clients
	Driver supports a userspace MPM
	Device supports configuring vdev MAC-addr on create.
```

---

### Post by Forbees on 2017-06-29
....bump?

---

### Post by Forbees on 2017-08-15
rebump?

---

### Post by vocx on 2017-08-15
> **Forbees said:**
> rebump?
Did you already try to compile the newest driver?

See this thread for reference: [https://ubuntuforums.org/showthread.php?t=2368526](https://ubuntuforums.org/showthread.php?t=2368526)

It seems lately many people have solved issues with the RTL8821AE chipset by installing these drivers.
[https://medium.com/@elmaxx/rtl8821ae...4-4c1286524afa]("https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa")

```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install

```

"These commands build and install the drivers for rtl8192ce, rtl8192se, rtl8192de, rtl8188ee, rtl8192ee, rtl8723ae, rtl8723be, and rtl8821ae, all in one go. Just in case the system doesn’t load the appropriate kernel module, you can execute the following command from within your rtlwifi_new directory


```

sudo modprobe rtl8821ae

```

Wait. Did you say RTL8812AE and not RTL8821AE? Is this the same chip, or was there an error copying the terminal output? I have seen many threads for 8821 (twenty one) but not 8812 (twelve).

---

### Post by Forbees on 2017-08-16
those are the exact steps i did to get rid of the dropping out and slow speeds (also sticking to wireless B.... i'd kill for N or AC to work)

for shits and giggles i ran through the steps again while the wifi wasn't working and it came back after reboot.


here's where i think the problem is, my cards chipset is RTL8812AE, but those drivers don't have it, the closest i saw was RTL8821AE, which is the driver i've modprobe'd.

so should i be modprobe'ing a different driver? i'll be sure to keep the steps in a text file so i can get it up and running reliably when it fails, but i'd prefer it just not fail at all lol (bonus points to get N or AC working)

---

### Post by Forbees on 2017-08-16
woops..... i thought this was the other post i've made where the computer will boot and just not detect the card... i'm running two problems lol

---

### Post by vocx on 2017-08-16
> **Forbees said:**
> those are the exact steps i did to get rid of the dropping out and slow speeds (also sticking to wireless B.... i'd kill for N or AC to work)

for shits and giggles i ran through the steps again while the wifi wasn't working and it came back after reboot.


here's where i think the problem is, my cards chipset **is RTL8812AE, but those drivers don't have it, the closest i saw was RTL8821AE**, which is the driver i've modprobe'd.

so should i be modprobe'ing a different driver? i'll be sure to keep the steps in a text file so i can get it up and running reliably when it fails, but i'd prefer it just not fail at all lol (bonus points to get N or AC working)
It is interesting that the kernel module you have and the driver are very close in number but are actually different.

Nevertheless, according to the output of the wireless script in your other thread, specifically the last part with the kernel messages, it seems you are loading the 8821 kernel module, but loading the correct 8812 firmware. So, it seems that as long as your card works, it's fine. Now, if you are not satisfied with the reliability of it, then it'd make sense for you to change it to a more stable one, preferably one with an Intel chipset. I have seen many Broadcom and Realtek chips that do work, but you need to investigate the chipset before buying so you don't end with the same issue again.
[https://ubuntuforums.org/showthread.php?t=2368840&p=13677006#post13677006](https://ubuntuforums.org/showthread.php?t=2368840&p=13677006#post13677006)

---

### Post by Forbees on 2017-08-17
so first boot since my last reply, the wifi was down again, did another modprobe and reboot now its back.... so unless you have a creative idea or someone else feels like chiming in my best bet is to get a more reliable card you think?

i have heard bad things about the realtek and broadcom chips, but sadly it was after i bought this one... i was kind of in a pinch and it was the only one in the store (should have just waited a week and ordered something)


do you have a good recommendation for a wifi card that will run wireless AC in ubuntu without headaches? i tried doing some googling earlier but wasn't finding something promising. ::sadface::

---

### Post by Forbees on 2017-08-26
chiming back in. other thread got my wifi reliable again. but still unable to connect to 5ghz

---

### Post by Forbees on 2017-11-20
latest distro fixed it. marking as solved

---

### Post by tengi on 2018-07-27
Hey. I am having the same issue. Mine is rtl8812ae + ubuntu18.04. I had very slow connections (~10mbps, 100mbps on my dual boot windows system).I did the above modprobe 8821ae. The network completely gone. I did modprobe -r 8821ae to remove it and reboot. But still no luck. What command you use to get the network back ? At least the original slow one (assume it is 802.11b like you said). Many thanks !

---

### Post by QIII on 2018-07-27
@ tengi:  This thread is very old.  Please start a new one of your own.  Feel free to include the URL to this thread in your new one.

Closed.

---

