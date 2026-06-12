---
title: "wireless randomly disconnects after connecting to a bluetooth device"
date: 2020-02-02
forum: Networking &amp; Wireless
---

### Post by thiagobarbosa48 on 2020-02-02
When I connect to any Bluetooth device the wireless connection starts to drop.


```
lspci -knn | grep Net -A2

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5325]
    Kernel driver in use: iwlwifi

```

The problem happened in Ubuntu 18 and persists in Ubuntu 19.10.

---

