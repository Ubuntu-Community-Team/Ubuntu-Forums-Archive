---
title: "Load balancing"
date: 2020-03-07
forum: Networking &amp; Wireless
---

### Post by pengyou2 on 2020-03-07
If a computer has 2 nics can Ubunto do load balancing internally? i.e. not need some additional hardware?

---

### Post by TheFu on 2020-03-08
Ubuntu isn't different from any other Linux distro.

That wouldn't be how I'd do it.  That isn't the main point for using a network load balancer.  Only one interface can have the primary outbound connection based on routing priority.

I'd bond the 2 NICs into 1 virtual NIC using network equipment capabilities, then the bandwidth from both would be available and if 1 NIC fails, the other would keep working.  Plus, this way the replies would be able to leave on the virtual NIC (either interface).

Do you want the Ubuntu system to be a router or pure LB, where will the programs be running?

---

