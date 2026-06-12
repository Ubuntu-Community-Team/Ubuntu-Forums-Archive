---
title: "How to disable wifi device?"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by mkor on 2007-05-28
Hi, I have wifi card in my laptop (interface ra0), which I do not use on daily basis and I want to turn it off. The button on my laptop does not work, so I have configured the network, assigning a particular address to the interface and unticked the interface in the network configuration window (to turn off the "roaming" mode). The result is in the /etc/network/interfaces as follows - no "auto ra0" (I have used "silly" sid/key settings - I am not going to use them):
```

iface ra0 inet static
address 192.168.1.77
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid NOTHING
wireless-key pppppppppp

```
However, when I start the system, the device is still active (checked by ifconfig) and sends some signal out (checked in the system monitor), which drives me crazy. The only solution I came up with was adding to rc.local explicit "down" command:
```

ifconfig ra0 down

```
but this is hardly satisfying... How can I stop it being started up properly?

By the way, I tried also completely deleting the ra0 entries from the interfaces file - no results.

Thanks,
Michal

---

