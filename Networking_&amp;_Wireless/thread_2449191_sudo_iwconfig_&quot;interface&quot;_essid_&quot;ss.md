---
title: "sudo iwconfig &quot;interface&quot; essid &quot;ssid&quot; interface not connecting to access point"
date: 2020-08-22
forum: Networking &amp; Wireless
---

### Post by atneal on 2020-08-22
UBUNTU 20.04
i run the command 

sudo iwconfig "interface name" essid "ssid"
the panda wireless adapter blinks but doiesnt connect to the access point.
any solutions?

---

### Post by wildmanne39 on 2020-08-22
Moved to Networking and Wireless.

---

### Post by chili555 on 2020-08-22
> **atneal said:**
> UBUNTU 20.04
i run the command 

sudo iwconfig "interface name" essid "ssid"
the panda wireless adapter blinks but doiesnt connect to the access point.
any solutions?Is there any encryption on the network; WPA2-AES, we hope? The wireless can't connect without the password. Moreover, iwconfig hasn't any way to connect with WPA or WPA2.

Why not use Network Manager?  

Is this a server? If so, use netplan.

---

