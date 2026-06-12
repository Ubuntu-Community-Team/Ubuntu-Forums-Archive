---
title: "ftp and firewalls"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by Hadesdarklord on 2008-05-30
I have to be doing something stupid...

I have a barebones Ubuntu 7.10 Server acting as my gateway/firewall. eth0 -> outward, eth1 -> inward

I am using iptables to do nat translation

-A PREROUTING -d external.ip.address.01 -i eth0 -p tcp -m tcp --dport 21 -j DNAT --to-destination internal.ip.add.05:21

Ubuntu 7.10 uses the nf_conntrack modules. I have nf_conntrack_ftp loaded into the kernel at startup

inside the network, I have an Ubuntu 6.06 machine running vsftpd, quietly waiting for a connection.

Whenever I connect, I get an error, stating that the ftp software cannot read from the control socket.

What am I missing?

---

