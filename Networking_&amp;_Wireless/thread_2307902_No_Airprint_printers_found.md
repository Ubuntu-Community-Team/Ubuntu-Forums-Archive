---
title: "No Airprint printers found"
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by cle-ziskind on 2015-12-29
As the title states - it happens with some servers at some times. Can some kind soul point me to a guide on diagnosing this?

All I know is that avahi is probably running:

# initctl list |grep avahi-daemon
avahi-daemon start/running

or is it?

avahi-cups-reload stop/waiting

---

