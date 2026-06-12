---
title: "SSH access to linux through isa server"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by ruiruas on 2007-03-09
Hi,
I have a windows network at work, but one of the servers is a linux machine. Since everything there passes through the isa server, I can't seem to access the linux machine with ssh. WHY?????

I created a windows "protocol" named SSH wich uses port 22, tcp, etc. and told the isa server to forward all requests to port 22 to the linux machine. The router/modem is a Cisco 870 wich is configured to forward all requests to the isa server.

When I try to connect, I get a window asking for my password on johndoe@111.111.11.11:22 and when I enter the password it asks me the same thing again (and again, and again...) :-(

Can someone tell me how to configure, both the isa server, and the router?

Oh! I forgot to say that I can access the linux machine with SSH when I'm inside Local Network, the problem only exists when I'm on the "outside" of the router and ISA.

Thanks in advance,

---

