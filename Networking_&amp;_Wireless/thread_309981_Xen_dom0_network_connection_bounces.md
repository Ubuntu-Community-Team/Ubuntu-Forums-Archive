---
title: "Xen dom0 network connection bounces"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by chewie124 on 2006-11-30
I have successfully setup Xen on a server I have, and successfully setup 2 Dapper guest domains on it.  One of the side effects of starting up Xen with the default network configuration (network-bridge) is that the network connection on dom0 becomes unavailable when the bridge is started up. 

To get around this, I used the second NIC to do the bridge, so I can still connect to dom0 via SSH.
[FONT="Courier New"]
eth0 <- Dom0 network connection
eth1 <- Xen network bridge interface[/FONT]

The problem that I'm seeing is that the network interface on eth0 keeps on intermittently bouncing;  ie, it'll go offline about once every hour or so, for 15-70 minutes.  

Anybody have any ideas what's going on?

TIA

---

