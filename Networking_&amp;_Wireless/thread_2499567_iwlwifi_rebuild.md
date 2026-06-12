---
title: "iwlwifi rebuild"
date: 2024-07-31
forum: Networking &amp; Wireless
---

### Post by lieta on 2024-07-31
Hi.
How to rebuild iwlwifi driver? Just need to enable CONFIG_IWLWIFI_DEBUG.

---

### Post by jeremy31 on 2024-07-31
What exactly are you trying to do?

---

### Post by lieta on 2024-08-01
I want to add debug logs to the driver. Station occasionally disconnects from access point and in wpa_supplicant log I see:
```

1722493569.290166: wlp0s20f3: Event DEAUTH (11) received
1722493569.290177: wlp0s20f3: Deauthentication notification
1722493569.290184: wlp0s20f3:  * reason 4 (DISASSOC_DUE_TO_INACTIVITY) locally_generated=1

```
[COLOR=#414141][FONT=sans-serif]although I'm constantly sending pings from AP to STA.[/FONT][/COLOR]

---

### Post by jeremy31 on 2024-08-01
Any result for ```
sudo dmesg | grep iwl
```

---

### Post by lieta on 2024-08-01
```

$ sudo dmesg | grep iwl
[    3.578637] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    3.586919] iwlwifi 0000:00:14.3: Detected crf-id 0x3617, cnv-id 0x20000302 wfpm id 0x80000000
[    3.586940] iwlwifi 0000:00:14.3: PCI dev a0f0/0074, rev=0x351, rfid=0x10a100
[    3.599954] iwlwifi 0000:00:14.3: api flags index 2 larger than supported by driver
[    3.599970] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.37
[    3.600590] iwlwifi 0000:00:14.3: loaded firmware version 77.2df8986f.0 QuZ-a0-hr-b0-77.ucode op_mode iwlmvm
[    4.027784] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x351
[    4.151320] iwlwifi 0000:00:14.3: Detected RF HR B5, rfid=0x10a100
[    4.217581] iwlwifi 0000:00:14.3: base HW address: 08:8e:90:09:45:39
[    4.249547] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
[    4.813983] iwlwifi 0000:00:14.3: Registered PHC clock: iwlwifi-PTP, with index: 0
[    7.047623] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[ 1961.759047] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[13802.777143] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[70989.919713] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[71418.672928] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[71590.006410] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[71590.006432] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[74209.336550] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[77691.245751] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[77720.617940] iwlwifi 0000:00:14.3: Unhandled alg: 0x703
[83390.820984] iwlwifi 0000:00:14.3: Unhandled alg: 0x703
[83990.755612] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[84230.730176] iwlwifi 0000:00:14.3: Unhandled alg: 0x707

```

Those "Unhandled alg" appear on authentication req:
```

[84230.710798] wlp0s20f3: authenticate with d4:01:c3:36:84:1e
[84230.718173] wlp0s20f3: send auth to d4:01:c3:36:84:1e (try 1/3)
[84230.730176] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[84230.851904] wlp0s20f3: send auth to d4:01:c3:36:84:1e (try 2/3)
[84230.866929] wlp0s20f3: authenticated
[84230.871960] wlp0s20f3: associate with d4:01:c3:36:84:1e (try 1/3)
[84230.883190] wlp0s20f3: RX AssocResp from d4:01:c3:36:84:1e (capab=0x1511 status=0 aid=3)
[84230.891588] wlp0s20f3: associated

```

---

### Post by currentshaft on 2024-08-01
foo

---

### Post by lieta on 2024-08-01
This is exactly where I started. In "How to debug?" capter: "To see more debug prints, CONFIG_IWLWIFI_DEBUG must be enabled."
I don't want to recompile the whole kernel, just iwlwifi driver.

---

### Post by currentshaft on 2024-08-01
.

---

### Post by currentshaft on 2024-08-01
.

---

### Post by lieta on 2024-08-01
> **currentshaft said:**
> If you run "iwconfig" does it say "Power Management: on"?
Was:
```

Power Management:on

```
Turned it off, testing now.

---

### Post by lieta on 2024-08-01
Supplicant log shows many
```
wlp0s20f3: Event BEACON_LOSS (53) received
```
followed by
```

1722493569.290166: wlp0s20f3: Event DEAUTH (11) received
1722493569.290177: wlp0s20f3: Deauthentication notification
1722493569.290184: wlp0s20f3:  * reason 4 (DISASSOC_DUE_TO_INACTIVITY) locally_generated=1

```
Doing trace-cmd log now.

---

### Post by currentshaft on 2024-08-01
.

---

### Post by lieta on 2024-08-01
Yes, there are other APs on the same channel. Where can you find a clean environment these days?
Changing channel is not an option. Station is not supposed to disconnect anyway.

---

### Post by jeremy31 on 2024-08-01
Ok, there are beacon loss events, I found a bug report earlier that involved Intel wifi and beacon loss causing disconnects, in terminal try
```
sudo -i
echo 5000 > /sys/module/mac80211/parameters/probe_wait_ms 
echo 50 > /sys/module/mac80211/parameters/beacon_loss_count
```
If that stops the issue, then ```
echo "option mac80211 beacon_loss_count=50" | sudo tee /etc/modprobe.d/mac80211.conf
echo "option mac80211 probe_wait_ms=5000" | sudo tee -a /etc/modprobe.d/mac80211.conf
```

A link to the bug report [https://bugzilla.kernel.org/show_bug.cgi?id=203709](https://bugzilla.kernel.org/show_bug.cgi?id=203709)

---

### Post by lieta on 2024-08-02
Thanks. That issue was reported on year 2019. :o

---

