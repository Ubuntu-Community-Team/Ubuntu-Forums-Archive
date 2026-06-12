---
title: "Preventing network detection on boot"
date: 2005-11-05
forum: Networking &amp; Wireless
---

### Post by rgould on 2005-11-05
I would like to disable network detection on startup so that the
system will boot much faster.
[URL="http://www0.risc.uni-linz.ac.at/systems/riscguide/laptop-netconfig/index_3.html"]
This page[/URL] mentions putting "noauto" below iface references,
and I have done so for eth0 and eth1 in my /etc/network/interfaces,
but they are still performing detection on boot.

Is there something else I have to do?

Here is my /etc/network/interfaces with comments removed.
```


auto lo
iface lo inet loopback

mapping hotplug
       script grep
       map eth1

iface eth1 inet dhcp
       noauto eth1

iface eth0 inet dhcp
       noauto eth0
wireless-essid torment

```
 
After a boot, running ifup eth1 (LAN) indicates that eth1 has already been brought up. Eth0 (wireless) is down after a boot.

---

