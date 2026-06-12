---
title: "DMZ apache logging"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by funkgui on 2008-02-18
Hi there,

I've set up a dmz with a web server behind it, the problem is that Apache logs
all external request as they are coming from 192.168.1.1 (the gateway). How
do I log the remote host instead of the internal IP address? 

Awstats in this case see only one visit (the gateway).

thanx

---

### Post by justleen on 2008-02-18
on top of my head: depends on your router forwarding.. 
If your router is not sending on any headers, apache will have no way of knowing where the original request came from..

---

### Post by funkgui on 2008-02-18
thanxs for your reply,

I'll explain more in detail what I'm doing:

                        Internet
                              |
  my LINUX router (1 NIC Public IP (eth1) - 1 NIC private IP(eth0))
                              |
  my Web Server (1 NIC private IP)


in my linux router machine I have those rule:

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -t nat -A PREROUTING -p tcp -d $MYPUBLIC_IP --dport 80 -j DNAT --to $MY_PRIVATE_WEB_SERVER_IP:80

all is working fine, but apache logs always show my gateway as client and not the real address.

thanx in advance
mARCO

---

