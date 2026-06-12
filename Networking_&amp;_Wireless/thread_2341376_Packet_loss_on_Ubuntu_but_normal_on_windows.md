---
title: "Packet loss on Ubuntu but normal on windows"
date: 2016-10-27
forum: Networking &amp; Wireless
---

### Post by mubeenchughtai on 2016-10-27
Hi,

I am facing packet loss on a destination  (64.154.41.100) when pinged on Ubuntu but on the same network, same  subnet public IP there is no packet loss. 

I've checked server CPU usage but it dosen't goes above 3-4%, have more then 50% free RAM.

What could be causing packet loss? what other troubleshooting steps can I take?

---

### Post by WedgeHG on 2016-10-27
Possible IP address conflict? i.e., something else on your subnet has the same IP as your Ubuntu machine. If that were the case you'd likely get the same symptoms pinging something on the local subnet (your router, for example).

Beyond that the only thing that comes to mind is to check for a bad Ethernet cable or switch port.

---

### Post by mubeenchughtai on 2016-10-28
IP address is static and there is no conflict. The issue disturbing is there is no loss on other destinations, so it cant be Ethernet or switch port.

---

