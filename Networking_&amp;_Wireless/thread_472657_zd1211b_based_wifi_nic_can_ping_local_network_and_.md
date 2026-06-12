---
title: "zd1211b based wifi nic can ping local network and gateway but not outside internet"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by ghmercado on 2007-06-13
hello folks hoping for some help here:

I got my zd1211 based wifi nic to work on my 7.04 Xubuntu. It is now recognized as eth0 which I setup via network-admin.

It can ping two of my other PCs on the network, namely 192.168.1.5 and 192.168.1.3, as well as my gateway router 192.168.1.10. However, when I try to ping an outside IP or surf using Ffox I get Network is unreachable.

Incidentally, thinking it was a DNS issue, I tried to follow OpenDNS' instructions for ubuntu :

[http://www.opendns.com/start/ubuntu.php]("http://www.opendns.com/start/ubuntu.php")

However, it appears I do not have a **/etc/resolv.conf** file, instead I have a **/etc/resolvconf** directory, which in turn contains the **update-libc.d** directory, which has one file, **avahi-daemon**, whatever that is. Everything is still in default, I just installed it today.

Anyway, I'm sure I'm just missing something to connect to the net, as apparently the NIC is working, its just not properly setup. Hope someone can help. Many thanks in advance.

---

### Post by ghmercado on 2007-06-13
this issue has been resolved.

---

