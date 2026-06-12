---
title: "Allow VPN access to local network"
date: 2019-01-04
forum: Networking &amp; Wireless
---

### Post by robertzito on 2019-01-04
I am running NordVPN on my Ubuntu 18.04, when it is on I cant access my network printer, when I shut it off I can print just fine. Is there a setting I am missing in the VPN or a route table I can create?

---

### Post by TheFu on 2019-01-05
I know that many corporate VPNs don't allow "split tunnels", which makes all traffic from the client to through the VPN - all traffic.  That would prevent LAN access.  When the VPN is active, you can check the routing table to see how NordVPN does stuff.  I hate the output for the new-fangled commands, but this should be pretty.  Please post it with code tags if you need help understanding the output.
```
route -n
```
If that command doesn't make a nicely formatted table, you can use 
```
ip route
``` which will make an ugly output, but with similar data. The first is easier to read.

---

### Post by The Cog on 2019-01-05
To get the full information, you really need to do two commands:
```
ip rule 
ip route list table all
```
Particularly, wireguard puts its default route in a custom routing table, so you don't see it with **route -n**. I don't know about NordVPN.

---

