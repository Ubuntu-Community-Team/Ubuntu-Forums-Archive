---
title: "e1000 trouble"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by mhennig on 2007-02-18
Hi all,

since I have upgraded to kernel

2.6.17-11-generic

there are problems with my Intel 82545EM card (the e1000 module). I still have a connection, but it is quite unstable. dmesg shows the following:

[17189761.636000] e1000: eth0: e1000_watchdog: NIC Link is Down
[17189763.292000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[17189781.588000] e1000: eth0: e1000_watchdog: NIC Link is Down
[17189783.308000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[17189795.568000] e1000: eth0: e1000_watchdog: NIC Link is Down
[17189797.188000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
.....


Because it coincides with a kernel upgrade, I suspect the new kernel (module) is flawed (but I haven't tried another kernel yet). Anyone else noticed this problem?

This is my card:
03:0e.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)

Cheers,
Matthias

---

