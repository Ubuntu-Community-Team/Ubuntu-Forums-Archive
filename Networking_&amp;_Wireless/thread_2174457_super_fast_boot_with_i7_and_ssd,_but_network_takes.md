---
title: "super fast boot with i7 and ssd, but network takes much time"
date: 2013-09-14
forum: Networking &amp; Wireless
---

### Post by celevra on 2013-09-14
Hi,

the system boots super fast, after 5seks everything is finished and network seems to be up:
[    5.054934] tg3 0000:02:00.0 p3p1: Link is up at 1000 Mbps, full duplex
[    5.054936] tg3 0000:02:00.0 p3p1: Flow control is off for TX and off for RX
[    5.054937] tg3 0000:02:00.0 p3p1: EEE is disabled

the systems uses a static ip
ipv6 is completely disabled, via sysctl.conf and grub

but, from the system a ping to the gateway is not possible, vice versa the same.
so the nfs mount times out and after about 20 seconds later, the system is reachable and everything is working, even the nfs mount is mountable.
no new entry in dmesg or syslog.
what is it, that takes so much time?

thanks for your help

---

