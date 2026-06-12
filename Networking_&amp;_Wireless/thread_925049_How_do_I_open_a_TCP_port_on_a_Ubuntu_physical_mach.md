---
title: "How do I open a TCP port on a Ubuntu physical machine for a Win virtual machine?"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by roxority on 2008-09-20
So here's my problem: I have a Windows 2003 guest virtual machine (32-bit) running under VMware Server 2.0 64-bit. The host machine running VMware Server is Ubuntu 8.04 (64-bit) where I have a custom web server running under TCP port 54321.

With both bridged and host-only networking, the (Windows) guest machine can ping the (Linux) host machine -- but cannot connect to the aforementioned TCP service (neither via Telnet nor a web browser). In both bridged and host-only networking scenarios, the two machines (virtual and physical) obviously belong to the same virtual LAN so they can ping each other. I suppose my Ubuntu is, per factory defaults, "over-configured / secured". How do I open this specific port for clients from these virtual networks or just from the LAN in general?

Without knowing much about iptables, I tried both

sudo iptables -I OUTPUT -p tcp --source-port 54321 -j ACCEPT

sudo iptables -I INPUT -p tcp --destination-port 54321 -j ACCEPT

which, from some googling, people sometimes seem to use for other ports like MySQL or BitTorrent. Didn't help with my particular problem in the VMware scenario I just described.

Any pointers gladly appreciated!

---

