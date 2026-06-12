---
title: "Change Primary Network Interface"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by Rossimo on 2007-08-11
Is there a way I can change what my primary network interface is? I'm currently connected to 2 networks, and I would like to pull a lot of the strain off of one network, and place it on the other.

---

### Post by donpaolo on 2007-08-11
You can specify in /etc/iftab the name (eth0,1,2,...) of every interface according to its MAC address.

man iftab for the format of the file.

---

