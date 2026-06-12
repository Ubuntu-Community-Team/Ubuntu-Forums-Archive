---
title: "Ubuntu 8.04 networking issues"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by gbjazzman on 2008-05-03
Hello,

This morning my Dell laptop running 8.04 was running flawless. Sometime after running the update this morning, networking broke.

Here's what I've determined so far.

The network manager icon in the gui is reporting Networking Disabled. ifconfig is only showing only lo. an lshw -C network show that networking is disabled for eth0 and eth1. /var/log/messages contains the line ADDRCONF(NETDEV_UP): eht0: link is not ready. I added eth0 and eth1 to /etc/network/interfaces and doing a /etc/init.d/networking restart give the error Ignoring unknown interace eth0=eht0

Anyone have any ideas I can try?

---

