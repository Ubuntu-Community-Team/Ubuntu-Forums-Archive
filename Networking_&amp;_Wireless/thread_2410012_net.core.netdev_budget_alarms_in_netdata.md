---
title: "net.core.netdev_budget alarms in netdata"
date: 2019-01-09
forum: Networking &amp; Wireless
---

### Post by daxterrr on 2019-01-09
Hi all,

Netdata has been throwing this alarm recently, so I decided to look into it.
[ATTACH=CONFIG]282165[/ATTACH]


I started reading the RHEL net perf tuning guide:
[https://access.redhat.com/sites/default/files/attachments/20150325_network_performance_tuning.pdf](https://access.redhat.com/sites/default/files/attachments/20150325_network_performance_tuning.pdf)

First, I checked /proc/net/softnet_stat and see that the third column is incrementing.
```

daxter@meerkat:~$ cat /proc/net/softnet_stat
00046b93 00000000 00000243 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0003c1a1 00000000 0000021c 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
00035181 00000000 000001cc 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0002fe73 00000000 000001df 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0002fac8 00000000 000001ca 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
0002e07e 00000000 000001c6 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
001b1a93 00000000 00001c31 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000
00047d63 00000000 000002be 00000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000

```

I then set net.core.netdev_budget to double the default of 300 as suggested in the tuning guide.
```

daxter@meerkat:~$ sysctl net.core.netdev_budget
net.core.netdev_budget = 600

```

Netdata is still throwing the alarm and the third column under /proc/net/softnet_stat is still ticking higher. What else can I do to resolve this? I've been searching Google and can't find anything promising to check into.

---

