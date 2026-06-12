---
title: "Problems with Intel AC 7260 wireless card"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by andrew192 on 2015-01-21
I'm running 14.10 on ASUS TP300L laptop with Intel AC 7260 card. Needless to say that it doesn't work.

lshw says: ```

                *-network UNCLAIMED
                description: Network controller
                product: Wireless 7260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: cb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f7800000-f7801fff
```

and iwconfig: ```
usb0      no wireless extensions.

lo        no wireless extensions.
```

Has anyone dealt with the same problem?

---

### Post by chili555 on 2015-01-21
> Needless to say that it doesn't work.Why do you say that? It works in 14.10 by default. If it isn't working, let's find out why:```
sudo modprobe iwlwifi
dmesg | grep iwl
rfkill list all
```

---

### Post by andrew192 on 2015-01-22
I've tried that, but dmesg | grep iwl shows nothing

rfkill says that nothing is blocked: ```
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Here is some additional info, that I think could be relevant:


```
lsmod | fgrep iwl
iwlwifi               182909  0 
cfg80211              510218  1 iwlwifi
```

```
dmesg | fgrep 80211 -A 3
[  743.251431] cfg80211: Calling CRDA to update world regulatory domain
[  743.260037] Intel(R) Wireless WiFi driver for Linux, in-tree:
[  743.260041] Copyright(c) 2003- 2014 Intel Corporation
[  743.275537] cfg80211: World regulatory domain updated:
[  743.275541] cfg80211:  DFS Master region: unset
[  743.275542] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  743.275544] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  743.275546] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  743.275547] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  743.275548] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  743.275550] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
```

```
sudo lhsw

...
*-network UNCLAIMED
             description: Network controller
             product: Wireless 7260
             vendor: Intel Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: cb
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:f7800000-f7801fff
...

```

---

### Post by andrew192 on 2015-01-22
I'm happy to say that with the nightly build of ubuntu gnome with kernel 3.18 everything's fine.
I think I'll use it for a while.

---

