---
title: "Multiple Gateways."
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by Einherjar on 2006-08-01
Due to administration policy, every computer on my network at work has to use DHCP. Unfortunately, the default gateway only allows HTTP and FTP traffic, so peer-to-peer applications are big No-No.

   A few days ago I discovered a NAT device with Internet access. I can open ports for my Dapper box, but I can't use it as my default gateway (otherwise, I won't be able to reach the servers I work with). So my question is...

   Is there any way I can configure aMule, Azureus or whatever the P2P application is, to use this NAT device as a gateway, while my default gateway remains the same as before? 

   PS. Excuse my lousy English, I'm trying to improve.

---

### Post by mips on 2006-08-01
One alternative is to make the NAT device your default route and then just add a normal route for your local network.

---

