---
title: "close door"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by Polo82 on 2007-05-06
Hi guys

a port-scanning result on my ubuntu dapper is:

```

631/tcp  open  ipp
8000/tcp open  http-alt
8081/tcp open  blackice-icecap

```

i'm looking informations about this services....anyone can tell me how close the doors??

thanks

Polo82

---

### Post by quux on 2007-05-06
Hi,

you can find the PIDs of the processes listening on those ports using ```
$ sudo fuser -n tcp 631
``` Here this returns ```
631/tcp:              6352
```
Then use ```
$ ps aux | grep 6352
``` to find the corresponding process info. Here this returns ```
cupsys    6352  0.0  0.2   4796  2160 ?        SNs  08:52   0:14 /usr/sbin/cupsd
``` which is the printing system daemon.

The same should work for the other ports. HTH

---

