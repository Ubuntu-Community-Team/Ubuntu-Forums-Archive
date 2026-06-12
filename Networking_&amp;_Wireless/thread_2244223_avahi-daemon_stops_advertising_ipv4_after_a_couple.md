---
title: "avahi-daemon stops advertising ipv4 after a couple of minutes of booting"
date: 2014-09-14
forum: Networking &amp; Wireless
---

### Post by franciscohs on 2014-09-14
I'm trying to troubleshooting avahi-daemon and I have this problem where everything works fine for about two minutes from starting (its always between 2m3s and 2m5s), and after that it stops.

Investigating I can see from osx that initially the name and IPv4 address is advertised correctly but after a while it's removed. There is no log or anything I can find when this happens. The second set of rmv and add is when I restart avahi-daemon, after boot and being started for the first time, avahi-daemon restart doesn't create an IPv4 record anymore.

```
OSX ~ #  dns-sd -G v4v6 ukyo.localDATE: ---Sun 14 Sep 2014---
14:26:19.523  ...STARTING...
Timestamp     A/R Flags if Hostname                               Address                                      TTL
14:26:21.400  Add     3  4 ukyo.local.                            10.1.1.8                                     120
14:26:21.400  Add     2  4 ukyo.local.                            FE80:0000:0000:0000:F66D:04FF:FED8:9737%en0  120
14:28:25.457  Rmv     0  4 ukyo.local.                            10.1.1.8                                     0


14:31:28.296  Rmv     0  4 ukyo.local.                            FE80:0000:0000:0000:F66D:04FF:FED8:9737%en0  0
14:31:29.523  Add     2  4 ukyo.local.                            FE80:0000:0000:0000:F66D:04FF:FED8:9737%en0  120

```

Cannot find any reason for this happening, anyone knows how to troubleshoot this? been looking for answers but cannot find anything similar.
avahi-daemon 0.6.30

---

