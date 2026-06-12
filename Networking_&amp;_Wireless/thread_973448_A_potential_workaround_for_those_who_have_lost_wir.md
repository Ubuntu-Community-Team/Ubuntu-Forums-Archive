---
title: "A potential workaround for those who have lost wireless in the last update"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by flaremon on 2008-11-06
It seems a recent update has broken wifi access for some people, myself included. Until Canonical issues an update, I have found that using an older kernel (2.6.24-21) works as a temporary fix. If anyone has a better solution, please post it in this thread.

---

### Post by Ferrat on 2008-11-06
For me I just removed network-manager, recompiled a new module for my wlan driver and use /etc/network/interfaces to launch the network, works ok

---

