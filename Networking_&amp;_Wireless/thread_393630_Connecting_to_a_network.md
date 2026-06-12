---
title: "Connecting to a network"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by zeroo on 2007-03-26
Okay I have a static ip and am trying to connect to a network.  The only problem is I dont know where in:
system-administrator-networking
to choose my network.  I feel really stupid but can someone please help me?

---

### Post by Floppyjoe on 2007-03-26
> **zeroo said:**
> Okay I have a static ip and am trying to connect to a network.  The only problem is I dont know where in:
system-administrator-networking
to choose my network.  I feel really stupid but can someone please help me?
You can specify your network in /etc/network/interfaces.
```
sudo gedit /etc/network/interfaces
```
Then change the essid to the network you want to connect to.

System/Administration/Networking shows you your different network interfaces such as wireless and wired.

---

