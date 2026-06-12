---
title: "dns port forwarding problem"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by funkgui on 2008-02-14
Hi guys I've got a problem with iptables and port forwarding of dns service.

this is the error:

[I]root@me:~ # dig mytestdomain.it @mypublicip.it
;; reply from unexpected source: 192.168.0.2#53, expected mypublicip#53[/I]

my iptables commands are simply these:

echo 1 >/proc/sys/net/ipv4/ip_forward
iptables -t nat -A PREROUTING -p tcp -d mypublicip --dport 53 -j DNAT --to 192.168.0.2:53
iptables -t nat -A PREROUTING -p udp -d mypublicip --dport 53 -j DNAT --to 192.168.0.2:53

any ideas?

thanxs mARCO

---

### Post by funkgui on 2008-02-14
I've solved masquerading the interface attached to the lan.

thanx

---

