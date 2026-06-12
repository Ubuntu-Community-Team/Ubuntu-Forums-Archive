---
title: "No eth0 connection"
date: 2016-12-22
forum: Networking &amp; Wireless
---

### Post by uyohn on 2016-12-22
Hello

I've just installed ubuntu srever 16.04 LTS, but network seems to be not working. Can't ping anything, including my router directly connected. Ifconfig returns only loopback and something called enp6s8. During installation it failed to automatically detect dhcp setting, so I did it manually. Those setting seems to be here, in output for ifconfig for enp6s8. 

Ifconfig looks like this: 
```

enp6s8   Link encap:Ethernet   HWaddr 00:11:11:77:60:a7
            inet addr:192.168.1.250   Bcast:192.168.1.255   Mask:255.255.255.0
            UP BROADCAST MULTICAST   MTU:1500   Metric:1
            RX packets:0   errors:0   dropped:0   overruns:0   frame:0
            TX packets:0   errors:0   dropped:0   overruns:0   carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B) TX bytes: 0 (0.0 B)

lo         Link encap:Local Loopback
            inet addr:127.0.0.1   Mask:255.0.0.0
            inet6 addr:   ::1/128 Scope:Host
            UP LOOPBACK RUNNING   MTU:65536   Metric:1
            RX packets:1791   errors:0   dropped:0   overruns:0   frame:0
            TX packets:1791   errors:0   dropped:0   overruns:0   carrier:0
            collisions:0 txqueuelen:1
            RX bytes:165408 (165.4 KB) TX bytes: 165408 (165.4 KB)

```

I've found official intel driver for my card "intel corporation 82562et/ez/6t/gz - pro/100 ve (lom)" but I can't compile it, because of "linux kernel source not configured - missing version.h. stop" error.

Please help.

---

### Post by gordintoronto on 2016-12-22
enp6s8 is your Ethernet connection. I think you are saying that you can't ping any of 192.168.1.1, 192.168.1.0, 192.168.168.1 and 192.168.168.1?

Have you tried using a different Ethernet cable?

---

