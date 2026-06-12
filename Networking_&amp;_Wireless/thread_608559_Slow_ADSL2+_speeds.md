---
title: "Slow ADSL2+ speeds"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by John_5 on 2007-11-10
Hey all,
my internet speed is 3x slower on Ubuntu than Windows XP, I have tried the following things:
-Disable IPv6
-Increase window size and other tweaks in sysctl.conf
```

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

```

Are there any other tweaks I need to do to get my internet speed better? 
Thanks in advance.

---

### Post by andlinux on 2007-11-10
I have the same problem but I have a simple adsl line. Disabled Ipv6 also but didn't help.
I better didn't upgrade to gutsy. :(

What I sometimes do is open vnc so that I can surf true my windowsXP computer.

---

### Post by Steve1961 on 2007-11-10
Try these firefox tweeks:

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

