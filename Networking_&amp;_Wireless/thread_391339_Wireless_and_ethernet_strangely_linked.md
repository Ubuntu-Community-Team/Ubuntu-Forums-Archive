---
title: "Wireless and ethernet strangely linked"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by Ephilei on 2007-03-23
I had my machine on ethernet until installing a madwifi wireless card. The installation seemed to go smoothly and DHCP gave me an IP. I could ping and ssh to the wireless IP fine. However, when unplugging the etherent cable, the wireless card losing all connections.

My only hypothesis is that the wireless card isn't really connected wirelessly, it's only connected to the network via the ethernet. 

Any suggestions would be greatly appreciated.

---

### Post by spd106 on 2007-03-23
If you look at the routing table you will be able to see which interface is being used as the default route to the gateway. If it's not pointed at ath0 then you won't be using the madwifi card.

```
ip route
```

---

### Post by Ephilei on 2007-03-23
The output for ip route is

```
192.168.1.0/24 dev ath0  proto kernel  scope link  src 192.168.1.113 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.64 
default via 192.168.1.254 dev eth0 
default via 192.168.1.254 dev ath0 
```

I don't know if that tells me the default gateway. Anyway, previously I was testing by pulling the ethernet cable out. Now I've disabled eth0 with ifconfig eth0 down and Ubuntu realized that I didn't want to use ethernet. 

It seems that if a cable is physically absent, Ubuntu should automatically switch the network adapter - at least until the cable is plugged in again. I'm not sure that qualifies as a "bug", but should I suggest this to the higher ups?  If so, how?

---

### Post by spd106 on 2007-03-24
You have two default routes, which is a bad thing. I strongly suggest that you remove one of them. This will not happen automagically, you need another utility such as Network Manager to do that.

These are your options:

1) Install Network Manager [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

2) Insert lines into the /etc/network/interfaces file to remove the gateway assigned by DHCP depending on which interface is currently plugged in (tricky).

or
 
3) Manually remove the route you don't want each time, or just make sure you only have  one interface active at any one time. i.e. chooses cable or wifi.

---

