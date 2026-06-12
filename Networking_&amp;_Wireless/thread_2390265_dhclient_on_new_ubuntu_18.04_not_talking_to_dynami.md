---
title: "dhclient on new ubuntu 18.04 not talking to dynamic dns"
date: 2018-04-27
forum: Networking &amp; Wireless
---

### Post by tomhorsley on 2018-04-27
For years and years I've been installing new ubuntu releases on virtual machines for testing and the new install always got the hostname added to the DNS server during the DHCP process. This morning I installed 18.04 desktop, and it certainly gets a network connection via DHCP, but the hostname didn't get added to the DNS server. Is there some magic handshake I need to configure somewhere to make this work? It has always just worked automatically before so I never had to dig up how to configure it.

DOH! Nevermind. Virtual machine got installed connected to the wrong bridge. Fixed that and dynamic DNS works fine.

---

