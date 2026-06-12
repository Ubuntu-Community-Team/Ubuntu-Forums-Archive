---
title: "Advanced Routing Question - how to set up subnets on my LAN"
date: 2016-12-12
forum: Networking &amp; Wireless
---

### Post by stlu on 2016-12-12
Hi,

This is what my network looks like right now:

```

                                LAN gateway to Internet
                                        192.168.2.1
                                             |
     +-----------------+---------------------+--------------------+---------------->192.168.2.{142-253}Other stuff
     |                 |                     |                    |
192.168.2.10     192.168.2.11          192.168.2.12         192.168.2.13
My laptop          VM host A            VM host B             VM host C
                       |                     |                    \---------> 192.168.2.{14-141}
                                                                              Bridged VMs C1-C128

```

I want to add more VMs, but my network is full.  So I can't bridge them to the network, I need to create subnets.
I have used up the whole LAN now and I am under pressure to free up some IP addresses.
This is what I can set up:
```
                                LAN gateway to Internet
                                        192.168.2.1
                                             |
     +-----------------+---------------------+----------------------+---------------------+---------------->192.168.2.{142-253}Other stuff
     |                 |                     |                      |                     |
192.168.2.10     192.168.2.11          192.168.2.12           192.168.2.13         192.168.2.(...)
My laptop          VM host A            VM host B               VM host C           VM Host D,E,F...
                  192.168.16.1         192.168.17.1           192.168.18.1
                       |                     |                      |
                       +192.168.16.{2-34}    +192.168.17.{2-34}     +192.168.18.{2-130}
                         VMs A1-A32            VMs B1-B32             VMs C1-C128

```

I want to be able to reach all the VMs from my laptop.  I don't want to have to ssh into the VM host and then again to the VM.

Problem: If the subnets are NAT'ed, then they will be able to reach the Internet, but then I can't reach them from my laptop.
Problem: If I make the VM's routable to the 192.168.2.0 network instead, then I will be able to reach them from my laptop, but then the gateway won't know how to route the traffic (it is a stupid gateway that I can't add routes to) and they will have no Internet access.

I have come up with some possible solutions, now I wonder which is the smartest for my scenario?
[LIST]
[*]I could create some complicated iptables rules for my VM hosts to route the sideways traffic, and NAT the outbound traffic 
[*]I could use a VPN inside my LAN 
[/LIST]
 
I know that if it were possible to put in a "smart" router that can be configured to know about subnets, this wouldn't be a problem.  However, I do not have that option available to me, I have to work with this stupid router.

What do you think would be best?

---

### Post by TheFu on 2016-12-12
Why not use a /23 subnet? Lots more IPs that way.

---

### Post by kpatz on 2016-12-12
You could create subnets, but you'd need a router that can route between them, or have a Linux box with 1 NIC per subnet and use that as a router.

Creating something bigger than a /24 is simpler.  172.16.x.x/16 is a private range you could use instead of a bunch of 192.168.x/24s.

What are you using as an Internet gateway?  If it's a "residential" router, it probably can't handle much bigger than a /24... but if you're using 254 IPs already, chances are you're using commercial grade equipment anyway.

---

