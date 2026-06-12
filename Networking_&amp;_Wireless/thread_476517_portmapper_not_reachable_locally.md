---
title: "portmapper not reachable locally"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by [cc]smart on 2007-06-17
i've noticed a few other threads related to portmapper and nfs reporting issues. in my case, playing around revealed one more detail. if i run rpcinfo -p <ubuntuhostname> from a remote machine against that ubuntu 7.04 i get a correct response. when i run rpcinfo -p or rpcinfo -p <ubuntuhostname> or rpcinfo -p localhost i get nothing at all. hosts.deny and hosts.allow are essentially empty and iptables -L reveals 0 rules and policy ACCEPT on all chains. /etc/default/portmap is all commented out.

---

