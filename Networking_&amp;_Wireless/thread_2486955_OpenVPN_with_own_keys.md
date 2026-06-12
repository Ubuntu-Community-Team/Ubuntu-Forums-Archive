---
title: "OpenVPN with own keys"
date: 2023-05-17
forum: Networking &amp; Wireless
---

### Post by Supermule on 2023-05-17
Hi,

I need to install OpenVPN on Ubuntu 22.04.2 LTS. I need to accept clients on port 1194 and once authenticated, all (!) traffic must be routed to an IP address behind the Ubuntu server. I have a server PEM key file and the client PEM files ready. So this should in theory be simple. But all guides assume that you do not have own certificates/keys. The goal is to have a client connect to my OpenVPN server using any OpenVPN compatible client (e.g. Open VPN Access client) and after authentication, they must have FULL access on the network behind the VPN server. So, can someone help with the above? What changes to the default OpenVPN installation on Ubuntu do I need to perform for this?
 
I have basic Linux and VPN knowledge.

Thanks.

Werner

---

