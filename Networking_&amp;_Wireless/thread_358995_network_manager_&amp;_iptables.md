---
title: "network manager &amp; iptables"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by mmc on 2007-02-11
hi, in the days before network manager i would call my iptables script as part of the interface initialization in /etc/network/interfaces  ... however network manager must have all interfaces disabled in /etc/network/interfaces as it controls the interfaces itself.

so how can i make network manager invoke my iptables scripts?

any kick in the right direction appreciated.

ta
mmc.

---

### Post by spd106 on 2007-02-11
You will have to do some more digging, but this page has a suggestion involving the /etc/NetworkManager/dispatcher.d folder. [http://www.ces.clemson.edu/linux/nm.shtml](http://www.ces.clemson.edu/linux/nm.shtml)

---

