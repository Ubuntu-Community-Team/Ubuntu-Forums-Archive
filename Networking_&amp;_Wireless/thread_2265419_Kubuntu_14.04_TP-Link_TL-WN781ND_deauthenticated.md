---
title: "Kubuntu 14.04 TP-Link TL-WN781ND deauthenticated"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by Tamas_Laloczki on 2015-02-15
Dear All, despite a week of trying I am unable to solve my problem. Lots of topics and solutions were checked and found to be useless for me.

I have a PCIe TL-WN781ND (ar9485). Previously not used with other OSes. I bought as it seemed to be a supported hw.

```
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
        Subsystem: Qualcomm Atheros Device 3118
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at fe900000 (64-bit, non-prefetchable) [size=512K]
        Expansion ROM at fe980000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k

```

```
laloczki@laloczki-box:~$ lsmod | grep ath
ath9k                 135567  0 
ath9k_common           25638  1 ath9k
ath9k_hw              453329  2 ath9k_common,ath9k
ath                    29249  3 ath9k_common,ath9k,ath9k_hw
mac80211              662298  2 ath9k,ath9k_hw
cfg80211              497209  4 ath,ath9k_common,ath9k,mac80211

```

Using Wicd or NM I get the following ( even with using "options ath9k nohwcrypt=1"):

```
[ 3712.668485] wlan0: authenticate with c0:c1:c0:78:fa:52
[ 3712.688858] wlan0: send auth to c0:c1:c0:78:fa:52 (try 1/3)
[ 3713.687188] wlan0: send auth to c0:c1:c0:78:fa:52 (try 2/3)
[ 3713.694533] wlan0: authenticated
[ 3713.695068] wlan0: associate with c0:c1:c0:78:fa:52 (try 1/3)
[ 3714.686927] wlan0: associate with c0:c1:c0:78:fa:52 (try 2/3)
[ 3715.674368] wlan0: associate with c0:c1:c0:78:fa:52 (try 3/3)
[ 3715.697775] wlan0: RX AssocResp from c0:c1:c0:78:fa:52 (capab=0x431 status=0 aid=2)
[ 3715.697867] wlan0: associated
[ 3716.901404] wlan0: deauthenticated from c0:c1:c0:78:fa:52 (Reason: 2=PREV_AUTH_NOT_VALID)
[ 3716.925549] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3716.925561] cfg80211: Restoring regulatory settings
[ 3716.925567] cfg80211: Kicking the queue
[ 3716.925573] cfg80211: Calling CRDA to update world regulatory domain
[ 3716.933138] cfg80211: Updating information on frequency 2412 MHz with regulatory rule:
[ 3716.933147] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933152] cfg80211: Updating information on frequency 2417 MHz with regulatory rule:
[ 3716.933156] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933159] cfg80211: Updating information on frequency 2422 MHz with regulatory rule:
[ 3716.933163] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933165] cfg80211: Updating information on frequency 2427 MHz with regulatory rule:
[ 3716.933169] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933172] cfg80211: Updating information on frequency 2432 MHz with regulatory rule:
[ 3716.933175] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933178] cfg80211: Updating information on frequency 2437 MHz with regulatory rule:
[ 3716.933181] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933184] cfg80211: Updating information on frequency 2442 MHz with regulatory rule:
[ 3716.933187] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933190] cfg80211: Updating information on frequency 2447 MHz with regulatory rule:
[ 3716.933193] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933196] cfg80211: Updating information on frequency 2452 MHz with regulatory rule:
[ 3716.933199] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933202] cfg80211: Updating information on frequency 2457 MHz with regulatory rule:
[ 3716.933205] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933208] cfg80211: Updating information on frequency 2462 MHz with regulatory rule:
[ 3716.933211] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933214] cfg80211: Updating information on frequency 2467 MHz with regulatory rule:
[ 3716.933217] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933220] cfg80211: Updating information on frequency 2472 MHz with regulatory rule:
[ 3716.933223] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 3716.933226] cfg80211: Disabling freq 2484 MHz
[ 3716.933256] cfg80211: World regulatory domain updated:
[ 3716.933259] cfg80211:  DFS Master region: unset
[ 3716.933263] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[ 3716.933267] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 3716.933272] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 3716.933276] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 3716.933280] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 3716.933283] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[ 3723.447943] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[ 3732.063303] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
Just to make sure that the card should work I created a Kubuntu 12.04 USB boot stick and checked, the card works perfectly.

-I returned to 14.04 with the standard linux-signed-image-3.13.0-45-generic kernel, edited the /etc/network/interfaces to bring up the card with fixed IP. Failed.
-I installed an old ubuntu kernel (3.2.45). Wicd with dhcp failed, the fix-IP /etc/network/interfaces method _WORKED._
-I tried new kernel versions as well. Failed.

What else can I try? My impression is that it is related to kernel/module and to Wicd/dhcp both.

---

### Post by praseodym on 2015-02-15
Deactivate the hardware encryption of the driver
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by Tamas_Laloczki on 2015-02-15
Thanks, I have already tried. Although it did not make any difference I retained this in [COLOR=#000000][FONT=Ubuntu Mono]/etc/modprobe.d/ath9k.conf.

[/FONT][/COLOR]

---

### Post by praseodym on 2015-02-15
Lets check
```

ifconfig -a
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by Tamas_Laloczki on 2015-02-18
Thanks for your helpfulness, on Sunday I replaced the atheros wifi card with a used noname RT2561 802.11g PCI which works at its 54Mb/s reliably. Once I'll have time I'll plug back the atheros card for a follow-up.

---

