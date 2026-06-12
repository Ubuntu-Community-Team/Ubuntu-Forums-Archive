---
title: "radvd can not work in Ubuntu 8.10"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by bonheurswp on 2008-11-24
Hi all,

I am newer for Ubuntu 8.10. when I want to run radvd, I faced errors as following:

Starting radvd: [Nov 24 10:04:28] radvd: IPv6 forwarding seems to be disabled, exiting failed.

IPv6 support must be enabled in the kernel for radvd to work.

Could someone help me?

Regards,

Weiping song

---

### Post by bonheurswp on 2008-12-01
Hi all,

I have fixed this problem by myself.

First, run "sudo sysctl -w net.ipv6.conf.all.forwarding=1"
Second, run "lsmod | grep ipv6", and you can find the process of ipv6.
third, run "sudo /etc/init.d/radvd start"

that should be okay.

Regards,

Weiping Song

---

