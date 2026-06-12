---
title: "Acer Spin 1 notebook  - wifi keeps losing internet access"
date: 2019-04-23
forum: Networking &amp; Wireless
---

### Post by santaclaws2 on 2019-04-23
Hello,

I have a strange problem with my Acer Spin 1 notebook  (running xubuntu 18.04).

It connects (wifi) to my home router with no problem at all but it keeps losing internet access after awhile (1 min - 10 min). When it happens, the wifi connection remains connected and I can even access my other LAN devices but I have no ping response from my router gateway (192.168.0.1) nor from any other internet IP (google & stuff). 

If I disconnect/reconnect the wifi connection, everything works fine again (unfortunately, for the same random period of 1 to 10 minutes). Btw, the rest of the LAN devices work great for years (hence I think there is no problem with my home router).

Thanks in advance for any clue.

---

### Post by santaclaws2 on 2019-04-24
Any help, please?

I've tried to disable the wifi card power management but nothing has changed (the LAN is reachable hence the wifi card is working properly though).

Could it be a routing problem? The output of the "route -n" command looks like this:

```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlp1s0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlp1s0

```

---

