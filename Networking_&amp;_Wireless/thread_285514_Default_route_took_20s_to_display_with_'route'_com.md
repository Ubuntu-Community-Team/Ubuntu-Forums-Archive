---
title: "Default route took 20s to display with 'route' command"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by Akhran on 2006-10-26
I have 2 NIC bonded together: 

# ifenslave bond0 eth0 eth1

When my eth0 is unplugged, the 'route' command took 20s to display the final route (ie. the default route). However, if eth1 is unplugged, the route command display the entire(including the default route) routing table almost instantly.

What could be the cause why it took much longer to display the default route when eth0 is unplugged?

PS. my network connectivity is down when eth0 is unplugged.

Please advise. 

Thanks !

---

