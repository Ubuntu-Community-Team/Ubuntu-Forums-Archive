---
title: "[ubuntu 14.04] wifi works but no internet connection in some cafes"
date: 2016-08-04
forum: Networking &amp; Wireless
---

### Post by cowpig2 on 2016-08-04
I've been unable to connect to the public wifi in certain places on my machine lately. I have a lenovo W550s with ubuntu 14.04. I try using **sudo network-manager restart** but it doesn't help. I'll connect to my phone's hotspot in the same place and it will work, and I'll have friends sitting next to me connected to the public wifi with it working perfectly.

Here's what dmesg says (and this loops a bunch of times before the machine seems to give up trying to connect):
```

[499848.459256] wlan0: authenticate with ac:f1:df:67:a4:a9
[499848.465799] wlan0: send auth to ac:f1:df:67:a4:a9 (try 1/3)
[499848.570113] wlan0: send auth to ac:f1:df:67:a4:a9 (try 2/3)
[499848.571931] wlan0: authenticated
[499848.572185] wlan0: associate with ac:f1:df:67:a4:a9 (try 1/3)
[499848.576320] wlan0: RX AssocResp from ac:f1:df:67:a4:a9 (capab=0x31 status=0 aid=8)
[499848.577323] wlan0: associated
[499848.877150] iwlwifi 0000:03:00.0: No association and the time event is over already...
[499848.877183] wlan0: Connection to AP ac:f1:df:67:a4:a9 lost
[499848.904772] cfg80211: Calling CRDA to update world regulatory domain
[499848.906667] cfg80211: World regulatory domain updated:
[499848.906670] cfg80211:  DFS Master region: unset
[499848.906671] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[499848.906672] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[499848.906674] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[499848.906675] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[499848.906675] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[499848.906676] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)

```

lspci -vv on my wireless controller:
```

03:00.0 Network controller: Intel Corporation Wireless 7265 (rev 99)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 45
    Region 0: Memory at f2000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi

```

rfkill:
```

rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
15: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

That's all I can think of adding. I'll be at this cafe for the next few hours if there's any other information I can get here that would help diagnose the problem!

---

