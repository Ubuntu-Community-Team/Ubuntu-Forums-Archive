---
title: "Load Balancing + Routing Question"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by Thildemar on 2008-08-05
Hi everyone,
I am trying to set up an Ubuntu box as a Load balancer to distribute traffic to two internet connections.  In addition I need to forward all incoming traffic from both connections to an internal system and send outgoing traffic going to a specific IP down a specific connection.

My setup is as follows:
eth0 - LAN connection - Static IP 192.168.10.1
eth1 - Cable connection - Static IP
eth2 - T1 connection - Static IP
Test system connected to eth0 - Static IP 192.168.10.100


I have the system load balancing per [http://computer.ebooktops.com/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/](http://computer.ebooktops.com/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/)  which works great.  Now I need to get the following:

A) Forward all incoming traffic to 192.168.10.100
B) Send outgoing traffic destined for a specific IP down the eth2 interface

Any tips on how to go about this would be much appriciated.

---

