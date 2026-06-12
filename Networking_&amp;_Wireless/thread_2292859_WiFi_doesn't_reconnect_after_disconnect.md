---
title: "WiFi doesn't reconnect after disconnect"
date: 2015-08-31
forum: Networking &amp; Wireless
---

### Post by Demiurgous on 2015-08-31
Initially, I thought I had the sleep/hibernate bug, but those solutions didn't seem to work. In addition, I noticed one day my router went out briefly, and my Dell m4800 refused to reconnect when the router came back on. So any time I drop a WiFi connection, it shows as reconnected, but there is no internet access at all.

Pertinent info typically requested in other threads that I've seen:
```
dmesg | grep iwl
[    2.965019] iwlwifi 0000:03:00.0: irq 46 for MSI/MSI-X
[    2.983581] iwlwifi 0000:03:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    2.998699] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    2.998765] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    2.999005] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    3.195494] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.564898] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    3.565251] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    6.815281] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[    6.815284] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   14.482763] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   14.482765] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  990.686046] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  990.686334] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  994.087955] iwlwifi 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  994.087956] iwlwifi 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
```

```
ls -al /lib/firmware | grep 7260
-rw-r--r--  1 root root  672352 Jul 31 06:06 iwlwifi-7260-10.ucode
-rw-r--r--  1 root root  782300 May 13 08:11 iwlwifi-7260-12.ucode
-rw-r--r--  1 root root  786920 Jul 31 06:06 iwlwifi-7260-13.ucode
-rw-r--r--  1 root root  683236 Nov 24  2014 iwlwifi-7260-7.ucode
-rw-r--r--  1 root root  679780 Dec  1  2014 iwlwifi-7260-8.ucode
-rw-r--r--  1 root root  680508 Dec  1  2014 iwlwifi-7260-9.ucode
```

```
lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
```

---

### Post by Demiurgous on 2015-09-01
Is there any additional information I can provide? Having to restart any time my router blinks (admittedly rare) or being unable to use suspend is a bit annoying.

---

