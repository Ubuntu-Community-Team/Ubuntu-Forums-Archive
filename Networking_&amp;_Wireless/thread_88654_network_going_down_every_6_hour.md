---
title: "network going down every 6 hour"
date: 2005-11-10
forum: Networking &amp; Wireless
---

### Post by integer on 2005-11-10
every six hours my eth0 decides to do: (from dmesg)
```
[4304672.682000] eth0: link down
[4304675.308000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4304675.340000] eth0: link down
[4304677.692000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
```
I have no idea why.
I just installed Breezy and I did not hav this problem in Hoary.
I'm guessing it may be something with DCHP. I do not have a /etc/dhclient.conf only a /etc/dhcp3/dhclient.conf is this normal? :???:

I have nothing going in cron and it happens every six hour +/- one or two minutes.

Any ideas?

---

### Post by teaker1s on 2005-11-10
try a static ip and manual dns if you still have problems then you know it's not dchp lease problem

---

