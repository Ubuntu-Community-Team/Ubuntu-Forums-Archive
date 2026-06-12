---
title: "Whole lan gone down. No connection."
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by drewu on 2007-02-18
I am having trouble connecting on my all my ubuntu (dapper) boxes. I am running DHCP from my router. Notably, I cannot connect even when I use my ubuntu live cd. Here is an output of ifconfig for eth0:

```
eth0[INDENT]Link encap:Ethernet HWaddr 00:0B:CD:AA:E7:98
inet6 addr: fe80::20b:cdff:feaa:e798/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:398 (398.0 b)
Interrupt:10 Base address:0xe000[/INDENT]
```

I had shut them down last night and they worked fine then. I am writing this from a mac because it is all I have left. My windoze box won't renew its ip under ipconif /renew either, but that may just be windoze because my mac has been restarted a few times today and there are no problems.
Thanks for your help.

---

### Post by TheWizzard on 2007-02-18
restart your router and try again.

---

### Post by drewu on 2007-02-18
Well I think that did it. I wonder why it didn't work when I tried before though..weird.
Thanks!

---

