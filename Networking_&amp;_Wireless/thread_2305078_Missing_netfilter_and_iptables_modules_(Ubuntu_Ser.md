---
title: "Missing netfilter and iptables modules (Ubuntu Server 14.04.3)?"
date: 2015-12-02
forum: Networking &amp; Wireless
---

### Post by kazso on 2015-12-02
Hi,

I've recently installed Ubuntu Server 14.04.3 LTS and compiled Squid 3.5.5 following [this guide]("http://cpcpasbar.blogspot.hu/p/cara-install-ubuntu-1404-lte.html") (i want transparent Squid with https support).
My problem is with the modules this guide refers to:

modprobe xt_TPROXY  
 modprobe xt_socket  
 modprobe nf_tproxy_core  
 modprobe xt_mark  
 modprobe nf_nat  
 modprobe nf_conntrack_ipv4  
 modprobe nf_conntrack  
 modprobe nf_defrag_ipv4  
 modprobe ipt_REDIRECT  
 modprobe iptable_nat

I can't find **nf_tproxy_core **and **ipt_REDIRECT **modules in this Ubuntu (i used Ubuntu 10.04 before, which has these modules).
modprobe nf_tproxy_core gives this error:
```
modprobe: FATAL: Module nf_tproxy_core not found.
```
modprobe ipt_REDIRECT gives no error, but lsmod doesn't show it either (the closest module is xt_REDIRECT, which is loaded).
How can i add these modules?

---

