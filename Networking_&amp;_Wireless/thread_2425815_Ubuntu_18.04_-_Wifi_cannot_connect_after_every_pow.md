---
title: "Ubuntu 18.04 - Wifi cannot connect after every poweroff"
date: 2019-08-30
forum: Networking &amp; Wireless
---

### Post by bilbatez on 2019-08-30
Hello,
I am using AsusTUF-FX505DT with Ubuntu 18.04 dual boot with Windows 10 which uses realtek 8822be wireless adapter to connect. Everytime I power-off or restart my laptop, I need to remove the kernel modules and load it back to connect to the wifi, otherwise it will just try to connect and then failed (or in some cases prompt me the password for the wifi over and over again). It's quite bothersome to reload the kernel modules everytime I boot up to ubuntu.

The things that I have tweak are the crda which I set to my own country code (after trying to google how to fix this issue) and the registry of windows for the time difference problem (I have set Linux rtc write to local before but changed it back).

```

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter
    Subsystem: AzureWave Device 2952
    Flags: bus master, fast devsel, latency 0, IRQ 60
    I/O ports at d000 [size=256]
    Memory at f7700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [148] Device Serial Number 00-e0-4c-ff-fe-b8-22-01
    Capabilities: [158] Latency Tolerance Reporting
    Capabilities: [160] L1 PM Substates
    Kernel driver in use: r8822be
    Kernel modules: rtwpci, r8822be

```

here is the driver message :
```

[   14.734765] rtw_pci 0000:03:00.0 wlp3s0: renamed from wlan0
[   39.610034] wlp3s0: authenticate with ac:84:c6:fa:6e:4e
[   39.610049] wlp3s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[   40.117692] wlp3s0: send auth to ac:84:c6:fa:6e:4e (try 1/3)
[   40.119096] wlp3s0: authenticated
[   40.122001] wlp3s0: associate with ac:84:c6:fa:6e:4e (try 1/3)
[   40.132153] wlp3s0: RX AssocResp from ac:84:c6:fa:6e:4e (capab=0x411 status=0 aid=1)
[   48.626393] wlp3s0: associated
[   48.626429] wlp3s0: deauthenticated from ac:84:c6:fa:6e:4e (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[   50.336520] wlp3s0: authenticate with ac:84:c6:fa:6e:4e
[   50.336534] wlp3s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[   50.837958] wlp3s0: send auth to ac:84:c6:fa:6e:4e (try 1/3)
[   50.841530] wlp3s0: authenticated
[   50.842011] wlp3s0: associate with ac:84:c6:fa:6e:4e (try 1/3)
[   50.852071] wlp3s0: RX AssocResp from ac:84:c6:fa:6e:4e (capab=0x411 status=0 aid=1)
[   59.310608] wlp3s0: associated
[   59.310653] wlp3s0: deauthenticated from ac:84:c6:fa:6e:4e (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[   65.187232] wlp3s0: authenticate with ac:84:c6:fa:6e:4e
[   65.187243] wlp3s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[   65.690377] wlp3s0: send auth to ac:84:c6:fa:6e:4e (try 1/3)
[   65.692660] wlp3s0: authenticated
[   65.694073] wlp3s0: associate with ac:84:c6:fa:6e:4e (try 1/3)
[   65.704600] wlp3s0: RX AssocResp from ac:84:c6:fa:6e:4e (capab=0x411 status=0 aid=1)
[   74.170121] wlp3s0: associated
[   74.170159] wlp3s0: deauthenticated from ac:84:c6:fa:6e:4e (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[   91.803504] wlp3s0: authenticate with ac:84:c6:fa:6e:4e
[   91.803517] wlp3s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[   92.306381] wlp3s0: send auth to ac:84:c6:fa:6e:4e (try 1/3)
[   92.307812] wlp3s0: authenticated
[   92.310070] wlp3s0: associate with ac:84:c6:fa:6e:4e (try 1/3)
[   92.320156] wlp3s0: RX AssocResp from ac:84:c6:fa:6e:4e (capab=0x411 status=0 aid=1)
[  100.770103] wlp3s0: associated
[  100.770134] wlp3s0: deauthenticated from ac:84:c6:fa:6e:4e (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[  170.238666] r8822be 0000:03:00.0 wlp3s0: renamed from wlan0
[  184.443427] wlp3s0: authenticate with ac:84:c6:fa:6e:4e
[  184.443436] wlp3s0: capabilities/regulatory prevented using AP HT/VHT configuration, downgraded
[  184.478122] wlp3s0: send auth to ac:84:c6:fa:6e:4e (try 1/3)
[  184.479549] wlp3s0: authenticated
[  184.486008] wlp3s0: associate with ac:84:c6:fa:6e:4e (try 1/3)
[  184.496242] wlp3s0: RX AssocResp from ac:84:c6:fa:6e:4e (capab=0x411 status=0 aid=1)
[  184.503744] wlp3s0: associated
[  184.636900] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready

```

I am a beginner in linux and I would really appreciate any help, because I made ubuntu as my default workspace. thank you!!

---

### Post by bilbatez on 2019-09-01
Update: after browsing the forum and found out that there is a script for wireless diagnostic as in this [thread]("https://ubuntuforums.org/showthread.php?t=370108"), here is my full [diagnostic]("https://pastebin.com/v7KwmN5x").
Something about failing in the 4way handshake timeout seems to be the problem which is weird considering the password is correct and everytime I reload the wireless kernel module it connected.
Is this a possible bug on the kernel module for r8822be or rtwpci?

---

