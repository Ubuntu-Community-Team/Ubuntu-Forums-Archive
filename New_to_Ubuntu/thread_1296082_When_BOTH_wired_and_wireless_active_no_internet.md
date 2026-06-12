---
title: "When BOTH wired and wireless active no internet"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by R_U_Q_R_U on 2009-10-20
I am using a Samsung NC10 with Ubuntu Netbook Remix 9.10 (but this problem is also noted on a DELL D600 running 9.04).

When running Ethernet only - Connects OK
When running Wireless G only - Connects OK
When running both Ethernet (eth0) and Wireless at same time the machines get two different IP addresses from DHCP router but have no access to internet.

I usually to all updates on the wired Ethernet connection. I noticed that with UNR I could leave both active and connect, but that changed after todays "Partial Upgrade"

Not too big a deal, I just turn off wireless when connected with wire, but is there a way to fix this? Is it a bug?  I am using an older Linksys G WRT54G router and have not tested on any other device.

---

### Post by Peter09 on 2009-10-20
post the output of the terminal command

```
route
```
when both devices are active.

---

