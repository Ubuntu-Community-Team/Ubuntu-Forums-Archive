---
title: "change adaptor name"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by sandyd on 2009-09-18
just curious.

my wireless connection is currently showing up as eth1. my ethernet is showing as eth0

is there some way to change it to wlan0?
i keep on getting confused between those two now....

---

### Post by plucky on 2009-09-18
> **carlee said:**
> just curious.

my wireless connection is currently showing up as eth1. my ethernet is showing as eth0

is there some way to change it to wlan0?
i keep on getting confused between those two now....

Post output of ```
cat /etc/udev/rules.d/70-persistent-net.rules
```

I think this is the file that keeps the names of your network interfaces.

Good Luck

---

### Post by sandyd on 2009-09-18
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x1698 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:19:f0:af:7a", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x432b (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:5e:38:66:c5", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

looks like it is this file. let me see how the edits do.

---

