---
title: "Stumped on setting up 2-interface firewall"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by dlk on 2007-03-11
Hello all:

I've recently set up an Ubuntu 6.06 machine with the intention of making it a firewall for a small office network connected to the Internet via an "always on" DSL connection. I've also installed shorewall, and read various how-tos and guides on configuring everything.

However, I'm stuck on what seems like an incredibly basic problem, but I can't seem to find an answer, and various things I've tried aren't working. Essentially, every guide says to give the firewall's external interface (eth0 in my case) my static external routable IP address, and to configure the internal interface (eth1 in my case) for the internal non-routable network, i.e., 192.168.X.X. All well and good.

The thing is, as far as I know, I only have a single static routable IP address, and that's already been assigned to the DSL modem/router itself as the WAN IP. Am I really also supposed to assign the same IP to the eth0 interface on the firewall?

If it matters, my DSL modem/router is currently what's providing DHCP and NAT for my internal network. I'm assuming the firewall will take over these functions (although I suppose I could run DHCP from my internal OS X Server as well.)

Thanks for any assistance.

---

