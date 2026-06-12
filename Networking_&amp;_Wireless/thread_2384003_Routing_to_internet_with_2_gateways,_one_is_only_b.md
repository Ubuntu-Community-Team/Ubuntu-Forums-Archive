---
title: "Routing to internet with 2 gateways, one is only backup gateway"
date: 2018-02-01
forum: Networking &amp; Wireless
---

### Post by advancedrouting on 2018-02-01
Following situation: 
Connection 1 Wired IP 192.168.0.110 GW 192.168.0.1
Connection 2 Wireless IP 192.168.8.5 GW 192.168.8.1

Gateway 1 Internetconnection is fast, but unreliable, sometimes gateway just can't route, interface stays connected
Gateway 2 Internetconnection is very slow, should only be used as backup. This means, if Interneet via 192.168.0.1 is available all traffic should be routed via that IP. Only if GW 192.168.0.1 doesn't reach internet it should be routed via 192.168.8.1
Is internet available again via 192.168.0.1 traffic should be routed again via this interface, even if this means breaking up existing connections.

All PCs with Internet-Access are connected to wired interface and thus have IPs in the range 192.168.0.0/24

I know how to configure routes with ip route add and metric stuff, however I think because wired network interface doesn't go down, it will always route via wired connection, because it reaches 192.168.0.1 BUT this gateway doesn't forward because its connection is broken. Thus internet connection for PC network won't work.

Can you help

---

### Post by tps-mail on 2018-02-01
My quick answer would be to check connectivity to a known host right across the primary link, and if you can't connect to it, bring that interface down so the route falls back to your secondary links...

---

