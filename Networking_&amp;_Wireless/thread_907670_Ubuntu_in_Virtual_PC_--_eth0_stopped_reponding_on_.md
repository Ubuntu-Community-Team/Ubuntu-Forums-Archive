---
title: "Ubuntu in Virtual PC -- eth0 stopped reponding on different network"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by not28 on 2008-09-01
Hi guys, a complicated situation here.

I set up an Ubuntu Server in Virtual PC (took some tweaks but it works wonders). I took the virtual disk to my school, but shared networking isn't allowing my Virtual machine to hit the school network (i'm getting loopback). I checked /etc/resolv.conf and it had my old nameservers/ips, so I cleared them out and replaced them with my school's DNS servers. I'm still getting 127.0.0.1 when I type ifconfig.

I haven't changed anything aside from the network that this server resides on. Does anybody have an idea as to how I could go about "resetting" eth0 so I can try resolving the network again?

---

### Post by not28 on 2008-09-01
I should also add when I type "ifconfig eth0" I get this: "eth0: ERROR while getting interface flags: No such device"

---

