---
title: "Ubuntu 15.10 Qualcomm Atheros Killer E220x Issue"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by joksanxfr on 2015-12-01
Hello,

I have a Qualcomm Atheros Killer E220x using Ubuntu 15.10. Once I boot using Ubuntu sometimes it will not recognize the card, disabling and enabling doesn't help. The only way to fix it thus far is to reboot, at that point it connects automatically upon bootup.

```
0a:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 10)
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
        Flags: bus master, fast devsel, latency 0, IRQ 140
        Memory at df100000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at d000 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: alx

```

```
Linux computer-name 4.2.0-18-generic #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

```
Ubuntu 15.10 \n \l
```

---

