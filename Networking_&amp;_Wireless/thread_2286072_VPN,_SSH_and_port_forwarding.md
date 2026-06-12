---
title: "VPN, SSH and port forwarding"
date: 2015-07-09
forum: Networking &amp; Wireless
---

### Post by henniebriel on 2015-07-09
Hi all.
Please help me with this problem.
I have a virtualbox ubuntu machine, connecting out via vpn (privateinternetaccess).
(The VM is set up as a bridged adapter. The box has its own IP.)
When I ssh from the local lan to this machine's ip address (with the vpn connected and active) everything works well.
When I try to come via the adsl/router (which is set up to do port forwarding to this machine) it doesn't connect when the vpn is connected. When I disconnect the vpn, all is good, and I can connect from my house.

Why can I ssh into this machine from the local lan and not from outside (via the forward port)
There are a few virtual machines running (all without vpn's) and they also connect through the forward ports?

Please help me to figure/sort this out.
Regards

---

### Post by TheFu on 2015-07-09
route

You didn't mention which type of networking is setup for the VM. NAT, host-only, bridged, ...?

---

### Post by henniebriel on 2015-07-10
Hi, sorry. Its a bridged adapter. The box has its own ip.

---

