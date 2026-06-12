---
title: "bad /etc/hosts file"
date: 2005-04-25
forum: Networking &amp; Wireless
---

### Post by bennettg on 2005-04-25
nOOb here.   after running the latest ubuntu ubdate, my firefox slowed to a crawl.   tried to play with the network settings and deleted the hosts.

where can i get a fresh copy of the /etc/hosts file to over write and correct the problem?

---

### Post by soce_32 on 2005-04-25
127.0.0.1       localhost.localdomain   localhost       shiner

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Copy that and replace "shiner" with your host name.

---

