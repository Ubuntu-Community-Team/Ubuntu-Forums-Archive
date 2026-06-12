---
title: "Multiple IPs - Cannot get it to work"
date: 2015-08-13
forum: Networking &amp; Wireless
---

### Post by Cochise on 2015-08-13
So I have a virtual server it has the following configuration:

eth0 - 10.10.2.134 address for LAN - working
eth1 - PUBLIC IP - working (a.b.c.134)
eth2 - PUBLIC IP - not working (a.b.c.148)

My gateway is a.b.c.129
The network is a.b.c.128/27

The two public IPs are on the same subnet, netmask, network etc, the only difference is 1 ends in .135 and the other .148, when I add the second one (.148) to my interfaces file as a new NIC (eth2) I cant ping it from another machine, this is down to the default route I think, however no matter what I try it doesn't work. I tried also to add it as an alias to eth1 (eth1:0) but again I cant ping it from another server.

What is the best solution, a second NIC or aliases? Anyone have any ideas on what routes to create etc.

The reason behind adding the second IP is I have a haproxy running and need to be able assign different WAN IPs to different frontends for SSL offloading.

---

### Post by bab1 on 2015-08-13
> **Cochise said:**
> So I have a virtual server it has the following configuration:

eth0 - 10.10.2.134 address for LAN - working
eth1 - PUBLIC IP - working (a.b.c.134)
eth2 - PUBLIC IP - not working (a.b.c.148)

My gateway is a.b.c.129
The network is a.b.c.128/27

The two public IPs are on the same subnet, netmask, network etc, the only difference is 1 ends in .135 and the other .148, when I add the second one (.148) to my interfaces file as a new NIC (eth2) I cant ping it from another machine, this is down to the default route I think, however no matter what I try it doesn't work. I tried also to add it as an alias to eth1 (eth1:0) but again I cant ping it from another server.

What is the best solution, a second NIC or aliases? Anyone have any ideas on what routes to create etc.

The reason behind adding the second IP is I have a haproxy running and need to be able assign different WAN IPs to different frontends for SSL offloading.
Normally you can't have 2 IP addresses in the same subnet being used by the same host unless you have the interfaces bonded into one entity.  If they are not bonded the expected result is just what you get.  One of the interfaces is set to down.  An alias interface is just want it says it is, not a separate interface at all. 

My guess is the haproxy should be upstream of multiple hosts not one with multiple interfaces in the same subnet.  Are you in control of the VM server or just a guest VPS?

---

### Post by Cochise on 2015-08-13
Figured it out was an issue with host firewall and aliases, all sorted now, had to allow traffic via the alias ip from the hypervisor.

---

