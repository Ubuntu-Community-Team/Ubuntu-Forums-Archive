---
title: "Quagga anycast setup, balancing TCP properly"
date: 2014-09-18
forum: Networking &amp; Wireless
---

### Post by xtremeqg on 2014-09-18
Currently I have several virtual machines, two "servers" running quagga which advertise their anycast address on an internal network via OSPF:

- server A
lo:0 static 192.168.56.250/32
eth0: dhcp 10.0.1.9/24
routing
10.0.1.0/24 dev eth0 src 10.0.1.9
192.168.56.0/24 via 10.0.1.254 dev eth0

- server B
lo:0 static 192.168.56.250/32
eth0: dhcp 10.0.1.91/24
routing
10.0.1.0/24 dev eth0 src 10.0.1.91
192.168.56.0/24 via 10.0.1.254 dev eth0

And one "router" running quagga and dnsmasq with DHCP on the internal network only (eth0)
eth0: static 10.0.1.254/24
eth1: 192.168.56.102/24
routing
10.0.1.0/24 dev eth0 src 10.0.1.254
192.168.56.0/24 dev eth1 src 192.168.56.102
192.168.56.250[INDENT]nexthop via 10.0.1.9 dev eth0 weight 1
    nexthop via 10.0.1.91 dev eth0 weight 1[/INDENT]

I've already set up all the ip_forward bits and enabled proxy_arp on eth1 of the router. At this point I have not configured anything in iptables, currently on all 3 machines they have default blank iptables. Pinging the anycast address (192.168.56.250) from the external subnet (192.168.56.0/24) works great and I can see packets hitting both servers in a balanced fashion. With a little bit of iptables masquerading and setting up a bridge interface on the router I was able to provide Internet access to both servers but...

I can't for the life of me figure out how to get TCP to work properly on the anycast address.

So far I've spent several days hunting the Internet for some kind of solution. I found various PDFs and PPT documents filled with case studies but nothing concrete. All of the iptable tutorials and sample configurations I've seen deal with balancing multiple Ethernet interfaces (for example, load sharing between two ISPs) and often require setting up separate routing tables which is not an option as the routes are generated automatically by quagga.

I know something can be done with conntrack... basically I would like to route TCP packets on a per-connection basis through the same hop that was chosen automatically on the initial SYN. How to forward packets through the same interface and use the default routing table... I have no clue.

Is there anyone able to assist me?

---

