---
title: "Network Manager OpenVPN does NOT pull"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by Che.SSL on 2008-11-07
Hi,
on the new Ubuntu 8.10 the network manager doesnt use the "pull"-directive anymore while connecting through OpenVPN - the tunnel is working though. Routes etc can`t be pushed anymore by an OpenVPN server.
Does anybody know how to fix this?

Thanks.

---

### Post by Che.SSL on 2008-11-07
Problem solved!
Just edit your VPN settings, click on the "IPv4 Settings" tab, then "Routes..." and activate "Ignore automatically obtained routes".

---

