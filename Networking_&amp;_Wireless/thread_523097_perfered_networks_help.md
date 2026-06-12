---
title: "perfered networks help"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by rigdzinthar on 2007-08-11
My WIFI chooses my neighbours network over my own,
can i disable my computer from choosing her network
how to?
thanks

---

### Post by rigdzinthar on 2007-08-11
bump

---

### Post by jmbargar on 2007-08-11
The network is in /etc/network/interfaces, only add a line like the follow in the interface definition:

wireless-essid the_name_of_your_wireless_network

and your computer will connect to the network you had specified there.

Best regards

---

