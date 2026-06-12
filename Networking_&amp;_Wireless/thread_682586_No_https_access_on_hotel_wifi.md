---
title: "No https access on hotel wifi"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by jenred on 2008-01-30
I'm traveling and have an encountered a somewhat strange wifi connection problem that I've never seen before -- usually have no problems connecting to various networks in various places.

For some reason any connection that requires ssl gets stuck in some sort of loading limbo.

This happens for yahoo mail. gmail, when connecting to my personal mail server (dovecot w/postfix - ssl).

My iphone connects and authenticates with no problem and my windows installation connects and authenticates no problem, thus I'm sure it's something isolated to the gutsy install.

Anyone have any ideas?

Thanks,
jen

---

### Post by jenred on 2008-01-30
I'm going to also add then when I try and access any https site in lynx I get:

SSL Error - No issuer was found-Continue?

---

### Post by jenred on 2008-01-30
Some additional information:

running:

```
/sbin/sysctl -a | grep tcp_window
```

results in:

```
error: permission denied on key 'net.ipv4.route.flush'
net.ipv4.tcp_window_scaling = 1
error: permission denied on key 'net.ipv6.route.flush'
error: "Invalid argument" reading key "fs.binfmt_misc.register"
```

---

### Post by jenred on 2008-02-01
Turns out this is an issue with TCP Window Scaling.

Fixes documented here:

[http://www.uluga.ubuntuforums.org/showthread.php?t=385094&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=385094&page=2)

---

