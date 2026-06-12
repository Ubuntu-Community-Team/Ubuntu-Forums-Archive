---
title: "/var/log/debug flooded with errors from wireless bcm43xx"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by KyleBrandt on 2007-07-10
My /var/log/debug and dmesg are always being flooded with the following error:
```
Jul 10 21:19:48 [My Hostname] kernel: [10296.668000] TKIP: received packet without ExtIV flag from 00:13:46:[##:##:##]
```

I also get:

```
J...kernel: [10605.768000] TKIP: replay detected: STA=00:14:bf:...... previous TSC 00000000063a received TSC 00000000006d
```

I have a Broadcom wireless card using the bcm43xx driver, and am using WPA.  I have installed the wpa supplicant and fw-cutter.  The wireless connection works fine.

Anyone have any ideas?

---

