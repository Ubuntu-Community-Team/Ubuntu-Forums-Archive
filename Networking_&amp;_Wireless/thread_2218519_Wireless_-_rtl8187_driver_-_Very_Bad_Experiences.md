---
title: "Wireless - rtl8187 driver - Very Bad Experiences"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by madbyte on 2014-04-21
Hi,

Yes, the rtl8187 driver is very bad. I was using ndiswrapper since Ubuntu 9.10, that solved my wifi problems with a very reliable connection. Sadly after upgrading to 13.10 ndiswrapper stop working in my system due a "FATAL module not found" when trying to load it, so I had to go back to the rtl8187. Now after upgrading to 14.04 I have to add new issues:

1) Using rtl8187: Now sometimes the connection is lost and I can't connect again, I'm getting this output from dmseg:

```

wlan0: deauthenticating from (MAC) by local choice (reason=3)
wlan0: deauthenticated from (MAC)  (Reason: 7)

```

2) Using ndiswrapper: It can be loaded now but for some reason it doesn't connect. After some failed attempts I'm getting nothing from dmseg:

```

ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,06/13/2008,5.1313.0613.2008) loaded
wlan0: ethernet device (MAC) using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8187.F.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
usbcore: registered new interface driver ndiswrapper

```

---

### Post by pdc on 2014-04-21
you might be best if this post was on the networking/wireless forum

and madbyte: have you checked posts such as these?

[http://ubuntuforums.org/showthread.php?t=2169120](http://ubuntuforums.org/showthread.php?t=2169120)

---

### Post by mörgæs on 2014-04-21
Moved.

---

### Post by madbyte on 2014-04-22
> **pdc said:**
> have you checked posts such as these?

[http://ubuntuforums.org/showthread.php?t=2169120](http://ubuntuforums.org/showthread.php?t=2169120)

I have read that post and didn't help.

Following more information:

My chipset is RTL8187L
 Ubuntu 32 bits.

**1) rtl8187:**

lsusb
```

Bus 001 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 005: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05d5:8001 Super Gate Technology Co., Ltd
Bus 003 Device 002: ID 0d9f:0002 Powercom Co., Ltd Black Knight PRO / WOW Uninterruptible Power Supply (Cypress HID->COM RS232)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

iwconfig
```

wlan0     IEEE 802.11bg  ESSID:"DGCR2"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: F8:D1:11:84:C5:F2   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:258  Invalid misc:47   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

dmesg | grep -e rtl -e wlan -e 80211 | tail -n25
```

[   40.817659] cfg80211: Calling CRDA to update world regulatory domain
[   40.827386] cfg80211: World regulatory domain updated:
[   40.827390] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   40.827393] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   40.827396] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   40.827398] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   40.827401] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   40.827403] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.014077] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   41.014293] ieee80211 phy0: hwaddr 00:15:af:09:e1:0e, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   41.025156] rtl8187: Customer ID is 0x00
[   41.031784] rtl8187: wireless switch is on
[   41.031832] usbcore: registered new interface driver rtl8187
[   48.672617] wlan0: authenticate with f8:d1:11:84:c5:f2
[   48.881728] wlan0: send auth to f8:d1:11:84:c5:f2 (try 1/3)
[   48.883913] wlan0: authenticated
[   48.884107] rtl8187 1-7.3:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   48.888056] wlan0: associate with f8:d1:11:84:c5:f2 (try 1/3)
[   48.890537] wlan0: RX AssocResp from f8:d1:11:84:c5:f2 (capab=0x411 status=0 aid=2)
[   48.891276] wlan0: associated

```

I already try *sudo iw reg set AR* but didn't help either.

My router is configured in WDS (WEP Open) to extend my WiFi range and there are 3/4 meters to my PC.
If the signal level is less than 50% I have connection but sometimes there is no Internet.
If the signal level is less than 20% I have connection but no Internet.
If the connection is lost I can't connect again and I need to restart my pc. In this case I tried:
```

sudo modprobe -r rtl8187
sudo modprobe rtl8187

```

But didn't help.

 **2) ndiswrapper:**
```

sudo modprobe -r rtl8187
sudo modprobe ndiswrapper

```

iwconfig
```

wlan0     IEEE 802.11g  ESSID:"DGCR2" 
          Mode:Managed  Frequency:2.417 GHz  Access Point: F8:D1:11:84:C5:F2  
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3 
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

```

dmesg | grep -e rtl -e wlan -e 80211 | tail -n25
```

[   48.883913] wlan0: authenticated
[   48.884107] rtl8187 1-7.3:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   48.888056] wlan0: associate with f8:d1:11:84:c5:f2 (try 1/3)
[   48.890537] wlan0: RX AssocResp from f8:d1:11:84:c5:f2 (capab=0x411 status=0 aid=2)
[   48.891276] wlan0: associated
[ 3960.556208] usbcore: deregistering interface driver rtl8187
[ 3960.564337] wlan0: deauthenticating from f8:d1:11:84:c5:f2 by local choice (reason=3)
[ 3960.910512] cfg80211: Calling CRDA to update world regulatory domain
[ 3960.918451] cfg80211: World regulatory domain updated:
[ 3960.918455] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3960.918458] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3960.918461] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3960.918463] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3960.918466] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3960.918468] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3970.296311] wlan0: ethernet device 00:15:af:09:e1:0e using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8187.F.conf
[ 3970.296349] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[ 3970.334338] cfg80211: Calling CRDA to update world regulatory domain
[ 3970.343788] cfg80211: World regulatory domain updated:
[ 3970.343793] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3970.343796] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3970.343798] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3970.343801] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3970.343803] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3970.343806] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

Using this driver I have no connection at all.

At this point, trying again with rtl8187
 ```

sudo modprobe -r ndiswrapper
sudo modprobe rtl8187

```

And trying to connect again:

dmesg | grep -e rtl -e wlan -e 80211 | tail -n25
```

[ 3970.334338] cfg80211: Calling CRDA to update world regulatory domain
[ 3970.343788] cfg80211: World regulatory domain updated:
[ 3970.343793] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3970.343796] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3970.343798] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3970.343801] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3970.343803] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3970.343806] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4225.069391] ndiswrapper: device wlan0 removed
[ 4230.569924] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 4230.570356] ieee80211 phy0: hwaddr 00:15:af:09:e1:0e, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 4230.584539] rtl8187: Customer ID is 0x00
[ 4230.592320] rtl8187: wireless switch is on
[ 4230.592383] usbcore: registered new interface driver rtl8187
[ 4276.140913] wlan0: authenticate with 78:6a:89:df:71:ec
[ 4276.249722] wlan0: send auth to 78:6a:89:df:71:ec (try 1/3)
[ 4276.251301] wlan0: authenticated
[ 4281.252079] wlan0: deauthenticating from 78:6a:89:df:71:ec by local choice (reason=3)
[ 4294.044118] wlan0: authenticate with 78:6a:89:df:71:ec
[ 4294.102228] wlan0: send auth to 78:6a:89:df:71:ec (try 1/3)
[ 4294.103885] wlan0: authenticated
[ 4299.224806] wlan0: deauthenticating from 78:6a:89:df:71:ec by local choice (reason=3)
[ 4309.778133] wlan0: authenticate with 78:6a:89:df:71:ec
[ 4309.829983] wlan0: send auth to 78:6a:89:df:71:ec (try 1/3)
[ 4309.831716] wlan0: authenticated

```

I can't connect and I need to restart my PC.

Thank you

---

### Post by rbuanno on 2014-12-15
I too have issues with this rtl8187 running ubuntu 14.04

I can connect however my speeds are EXTREMELY slow. I never surpass 1M speeds...
I hope someone can help us with our issues. I got this rtl8187 because it was "linux supported".
I mean it works.. but no where near as good as it should. The same device blows doors off in windows.

Someone help us with this rtl8187!

-----------EDIT------------
In case you didn't see my other thread I have going about this same chipset.
[COLOR=#000000] [/COLOR][https://help.ubuntu.com/community/Ha...rdsRealTek#USB]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB")
This basically has been doing horrible for awhile.
I don't understand why everyone seems to love this adapter...

---

