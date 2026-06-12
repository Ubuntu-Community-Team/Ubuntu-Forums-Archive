---
title: "iptables and NAT"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by vortmax on 2008-11-25
I'm sure this is asked a lot, but I've read all the how to's and other posts and still can't get it to work.

I'm attempting to get NAT to work with IPtables on ubuntu 8.04

Here are my iptables rules:

```

Chain PREROUTING (policy ACCEPT 49 packets, 6557 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DNAT       tcp  --  eth0   any     anywhere             192.168.3.251            tcp dpt:24 to:172.16.16.7:22

Chain POSTROUTING (policy ACCEPT 12 packets, 888 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 12 packets, 888 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain INPUT (policy DROP 5 packets, 560 bytes)
 pkts bytes target     prot opt in     out     source               destination
  275 32153 ACCEPT     all  --  eth0   any     anywhere             anywhere
   16  1472 ACCEPT     all  --  lo     any     anywhere             anywhere
    7   588 ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 DROP       all  --  eth1   any     anywhere             anywhere            state INVALID,NEW,UNTRACKED

Chain OUTPUT (policy ACCEPT 217 packets, 99454 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:domain
   18  3120 ACCEPT     all  --  any    eth0    anywhere             192.168.1.93
    0     0 DROP       all  --  any    eth0    anywhere             192.168.0.0/16      state INVALID,NEW,UNTRACKED


```

right now I'm just trying to nat over port 24 on eth0 to port 22 on an internal IP.  I've added LOG targets and it appears the DNAT rule is being caught, but nothing is being forwarded through.  I do have the proper routing tables in place and I can access 172.16.16.7:22 from this host.

---

### Post by superprash2003 on 2008-11-25
you can take ideas from this
Case 2 :

To DNAT the incoming port 8080 at 203.158.26.29 at eth2 to the DMZ station 192.168.10.188 web server ( port 80 )

    # /sbin/iptables -t nat -A PREROUTING -i eth2 -d 192.168.10.188 -j DNAT --to 203.158.26.29:8080

[http://10network.justk2.com/2008/05/linux-firewall-iptables-nat.html](http://10network.justk2.com/2008/05/linux-firewall-iptables-nat.html)

---

### Post by vortmax on 2008-11-25
thanks,
amazingly enough my iptables were correct.  I was just missing a routing entry in one of my routers down the line.

---

