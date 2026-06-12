---
title: "Can't connect to network after crash - unbuntu 7.10 server"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by phylae on 2008-04-10
**RESOLVED**


I have a server with Ubuntu 7.10.

The server has 4 Ethernet ports, and I was using bonding for load balancing. This has all been working fine for several months. Two days ago, the server stopped responding to ssh. So I did a hard restart and tried again--that didn't help.

Now, I THINK the server MIGHT have halted itself because of overheating, and that was why it lost the connection in the first place. However, I am not positive. I have made some adjustments and now the CPU and case temperature are both below 35 Celsius. (Before the CPU temp was often in the 60s.)

My problem is this. Ever since I brought the server back up, it hasn't been able to connect to the network. In the process of trying to figure out what happened, I decide to get rid of the network bonding. So I only added 1 port to /etc/network/interfaces and I commented all the bonding stuff in /etc/modprobe/aliases and /etc/modprobe/arch/i386. However, I still can't connect to the network.

Everything is set up to use DHCP. None of the settings have changed on the router.

Is there someway to have Ubuntu reinstall all the network related stuff? Or do you have any suggestions for how I can fix this?

Thanks

---

### Post by phylae on 2008-04-10
Ok. now I feel stupid. I had two network cables fail at the exact same time. That was the whole problem. I guess I shouldn't assume that just because I try two different cables there won't be a problem!

---

