---
title: "Extremely slow network performance"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by klobuczek on 2008-08-02
I am having a very slow network performance on my Ubuntu 8.04.
My hardware is Dell Latitude D820. I have done many tests with the hardware and the bad performance occurs only in one scenario:

Ubuntu 8.04 plain - 3% of the ISP Bandwidth
Windows XP  - 100% ISP Bandwidth
Ubuntu 8.04 on VirtualBox on Windows XP host - 100% Bandwidth
Ubuntu 8.04 + Cisco VPN connection - 100% Bandwidth
Ubuntu 8.04 plain on old Dell Inspiron 8100 - 100%

All my ubuntu configurations are pretty much identical. I suspect that this has to do with the drivers for the network card. But then why is the problem gone as soon as I connect to VPN.

Any ideas?

---

### Post by casevh on 2008-08-02
The Cisco VPN client decreases the MTU of network interface. Try changing the MTU and see if that makes a difference.

sudo ifconfig eth0 mtu 1400

casevh

---

### Post by klobuczek on 2008-08-03
MTU 1400 or 1356 (that's what my cisco vpn client uses) increases the performance just minimally to 5% of the available ISP bandwidth.

---

