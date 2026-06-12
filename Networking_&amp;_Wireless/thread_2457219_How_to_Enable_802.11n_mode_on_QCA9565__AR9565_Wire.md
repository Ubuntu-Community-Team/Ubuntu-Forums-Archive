---
title: "How to Enable 802.11n mode on QCA9565 / AR9565 Wireless  Adapter in Ubuntu 20.04"
date: 2021-01-28
forum: Networking &amp; Wireless
---

### Post by tahoua on 2021-01-28
I have an Acer E3-111 notebook running Ubuntu 20.04 which does not seem to be able to get more than 50 Mbps download speed on the 2.4GHz band of my wifi router despite having an 802.11n adapter.  The router is set to handle multiple speeds including g & n.

```
$ sudo lshw -class network
``` renders:
```
  *-network                 
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: 18:cf:5e:7d:0a:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=5.8.0-40-generic firmware=N/A ip=10.0.0.225 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:90600000-9067ffff memory:90680000-9068ffff
```

which confirms that the correct driver, ath9k, is in use for the QCA9565 / AR9565 Wireless Network Adapter.

However, ```
$ iwlist scan
``` renders:
```
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s, 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
```
which seems to me to indicate that 802.11n is not enabled on the network adapter, because if it was enabled the bit rates would be much higher.

I searched online and found that people had a similar problem with the QCA9565 on Windows machines and were able to resolve it by enabling 802.11n mode for the adapter.

Is there a way in Ubuntu 20.04 I can more clearly see whether or not 802.11n is enabled in the wifi adapter configuration?  And if it is not, how do I enable it?

---

### Post by chili555 on 2021-01-28
The bitrates you quoted above relate to the wireless access point, usually a wireless router, and not your computer's wireless card. Your router is saying, in effect, I can do these nice, easy and slow rates and once we know more about each other, we can negotiate higher rates.

Please run the terminal command:

```
iw list | grep HT
```

We hope you see lines like these:

```
HT20/HT40
			RX HT20 SGI
			RX HT40 SGI
			DSSS/CCK HT40
		HT Max RX data rate: 300 Mbps
		HT TX/RX MCS rate indexes supported: 0-15
		Bitrates (non-HT):
			HT20/HT40
			RX HT20 SGI
			RX HT40 SGI
			DSSS/CCK HT40
		HT Max RX data rate: 300 Mbps
		HT TX/RX MCS rate indexes supported: 0-15
		VHT Capabilities (0x038071a0):
		VHT RX MCS set:
		VHT RX highest supported: 0 Mbps
		VHT TX MCS set:
		VHT TX highest supported: 0 Mbps
		Bitrates (non-HT):
	HT Capability overrides:
	Device supports HT-IBSS.
		* [ VHT_IBSS ]: VHT-IBSS
```HT20 is high throughput at 20mHz bandwidth, HT40 is 40 mHz bandwidth and VHT is very high throughtput, typically 802.11ac. I don't believe your device is 802.11ac capable so that you will probably not see VHT above.

You can see what rate your wireless device and your router have negotiated with:

```
iwconfig
```

For example:

```
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xxxx
          [COLOR="#FF0000"]Bit Rate=866.7 Mb/s  [/COLOR] Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:281   Missed beacon:0


```Your router will not likely negotiate higher bitrates if your router uses TKIP. The well-known suggestions apply here.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router.

---

