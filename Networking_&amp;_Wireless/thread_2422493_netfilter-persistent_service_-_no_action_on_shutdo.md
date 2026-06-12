---
title: "netfilter-persistent service - no action on shutdown"
date: 2019-07-08
forum: Networking &amp; Wireless
---

### Post by 7-mike-x on 2019-07-08
On Ubuntu 16.04 server, I notice that the netfilter-persistent service is restoring my iptables at startup - but it does not save them during shutdown.  So any changes made to iptables are lost at reboot, unless explicitly saved (to the correct file) with the iptables-save command.
I'm wondering if this is Working As Designed, or something mis-configured on my system.
Shouldn't the equivalent of [FONT=courier new]systemctl stop netfilter-persistent[/FONT] be executed as part of shutdown?

---

