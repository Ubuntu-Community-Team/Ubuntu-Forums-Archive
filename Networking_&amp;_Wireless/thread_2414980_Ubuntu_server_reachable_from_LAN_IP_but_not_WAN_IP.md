---
title: "Ubuntu server reachable from LAN IP but not WAN IP within network"
date: 2019-03-18
forum: Networking &amp; Wireless
---

### Post by kose-onur on 2019-03-18
Hello,
I'm building an ubuntu server at home for a nodejs project.
I've configured DMZ settings of my DSL modem to route WAN IP to the server's LAN IP and it works fine.
The problem is when I try to reach server via WAN IP from any of local computers I can't reach the server but I can reach the server via it's LAN IP from browser and SSH etc.
Server is also reachable from WAN IP from outside of the local network.
I know it's a bit confusing but I'd appreciate any help.

---

### Post by SeijiSensei on 2019-03-18
Many consumer routers can't handle internal requests that are intended for the router's external interface. Drove me crazy the first time I encountered such a device.

Can you see the server over the LAN if you use it's internal LAN address rather than its external address?

---

### Post by Doug S on 2019-03-18
It is my understanding that the situation you describe is fairly normal.

For those of us that desire to use our same WAN FQDNs (Fully Qualified Domain Names) on our LAN, we either override DNS results via the /etc/hosts file or run an internal DNS giving our internal IPs.
Myself, I run an internel bind9 DNS server.

---

### Post by kose-onur on 2019-03-19
> **SeijiSensei said:**
> Can you see the server over the LAN if you use it's internal LAN address rather than its external address?

Yes I can use the server with it's LAN address anyways.
The point that I'd like to use with WAN address is this server runs a nodejs API and I need to do some performance tests from my local computers.

---

### Post by garyed on 2019-03-19
I just encountered the same problem with my Apache server & it evidently has to do with the router that gives out the LAN ip addresses. I couldn't figure out a way around it but when I switched routers I was able to access my server from my local computers using the WAN address. There could be a setting in the router but I couldn't find any so my guess is that your problem is router specific.

---

