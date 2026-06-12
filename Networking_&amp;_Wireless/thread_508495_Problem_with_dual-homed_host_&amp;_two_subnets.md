---
title: "Problem with dual-homed host &amp; two subnets"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by EmmEff on 2007-07-24
I have a dual-homed host (eth0 & eth1).

eth0 is 192.168.0.1 is connected to my home network and has Internet access.

eth1 is 10.0.0.1.  I would like hosts on this subnet to have Internet access routed through eth0 (192.168.0.1).

I have enabled forwarding in /etc/sysctl.conf (and rebooted) on the dual-homed host, but hosts in the 10.x.x.x subnet still cannot access the Internet.

Hosts in the 10.x.x.x network have the default gateway set to 10.0.0.1.

Is there an obvious step I am missing?  Since I don't need NAT, I thought I could get away with simple routing.

Thanks in advance.

---

### Post by gangolli on 2007-07-24
Several things.

Hosts on the 10 subnet should have their default route set to the 10.0.0.1, the interface of the dual-homed host which is serving as the gateway on that net.   

Make sure the dual-homed host has forwarding set up in both directions.

Since 192.168.0 is also private, it must be the case that you already have another router going to the internet at large that is doing NAT.

Make sure that internet router will NAT the 10 net addresses as well because since you're not doing NAT at the dual-homed host, the source address of traffic from hosts on this net is going to remain the original host address on that 10 net when it crosses onto the 192.168.0 net.  Your router may work better if you make the 10 net a 192.168.1 class C instead.  Not sure if this is an option for you.

Finally, you must get traffic back to the 10 net from the 192.168 net.  Your default route on the 192.168 net is going to be your internet router, so that is not going to work.  You have to set up a specific route for addresses on your 10 net to go to 192.168.0.1

If you have other hosts on the 192.168.0 net you should first try to test traffic between one of those and a host on your 10 net to make sure that leg is working before trying to get to the net at large.  This will separate issues you are facing at your internet router from ones you are facing at the dual-homed host.

---

### Post by EmmEff on 2007-07-24
I think my problem was the missing route from 192.168.0.1 to 10.x.x.x.  This seems like the logical reason.

Using tcpdump, I was able to see traffic going from 10.x.x.x to 192.168.0.x but not returning back to 10.x.x.x.

I will give this a try ASAP but thank you in advance for the help.  I think you nailed it.

---

### Post by Mr. C. on 2007-07-24
If you have trouble still, show your route table:

```
netstat -rn
```

MrC

---

