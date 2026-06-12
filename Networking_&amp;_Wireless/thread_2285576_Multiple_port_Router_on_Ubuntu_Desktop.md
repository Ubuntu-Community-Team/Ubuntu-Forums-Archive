---
title: "Multiple port Router on Ubuntu Desktop"
date: 2015-07-07
forum: Networking &amp; Wireless
---

### Post by risva on 2015-07-07
I am wanting to configure router cum firewall in our small office complex on ubuntu machine. I have read number of threads on this, but what is typical in my requirement is that i want to subnet the ip block alloted to my branch into subnets for various sections and apply traffic based firewall rules on this. the requirement is as follows:  

eth0 (ip pool for my branch): A.B.C.0 /24       (external facing port) 
eth1 (subnet for section A) : A.B.C.32 /27       (internal facing port) 
eth2 (subnet for section B) : A.B.C.64 /27       (internal facing port) 
eth3 (subnet for section C) : A.B.C.96 /27       (internal facing port)  

general rules that i need to configure for firewall are:  

eth1,eth2,eth3    TO   eth0    FOR   service 80, 2000, 91       ALLOW 
eth0,eth2, eth3   TO   eth1    FOR   service 80, 2000, 91      ALLOW 
deny rest all  

I request if anyone can please guide me on this !!

---

### Post by bab1 on 2015-07-07
> **risva said:**
> I am wanting to configure router cum firewall in our small office complex on ubuntu machine. I have read number of threads on this, but what is typical in my requirement is that i want to subnet the ip block alloted to my branch into subnets for various sections and apply traffic based firewall rules on this. the requirement is as follows:  

eth0 (ip pool for my branch): A.B.C.0 /24       (external facing port) 
eth1 (subnet for section A) : A.B.C.32 /27       (internal facing port) 
eth2 (subnet for section B) : A.B.C.64 /27       (internal facing port) 
eth3 (subnet for section C) : A.B.C.96 /27       (internal facing port)  

general rules that i need to configure for firewall are:  

eth1,eth2,eth3    TO   eth0    FOR   service 80, 2000, 91       ALLOW 
eth0,eth2, eth3   TO   eth1    FOR   service 80, 2000, 91      ALLOW 
deny rest all  

I request if anyone can please guide me on this !!
Your network as you say is as you say is A.B.C.0 /24  -- it is entirely on the LAN side.  The WAN side IP address is the ISP's responsibility to assign an IP address.

The subnets would be this:
eth1 (subnet for section 1) : A.B.C.0 /27  (IP range 0 - 31
eth2 (subnet for section 2) : A.B.C.63 /27 (IP range 32 - 63)
eth3 (subnet for section 3) : A.B.C.93 /27  (IP range 64 - 93)

This will leave the IP range of 94 to 255 unused with /27 blocks.  This is 161 addresses unused; more unused than used.  Is this want you want?  You could subnet using /26 which will give you a 64 number range that would allow you 4 subnets.  The unused portion would be 64 addresses unused with /26 blocks.

In other words your choice uses 32 address blocks or you could use a 64 address blocks with less waste.  Or Maybe you have something else in mind for the remaining addresses.

Why are you separating these addresses if you are allowing the same service to all.  I don't see the need for the complexity.  If you do use all 3 LAN interfaces you need to have separation, as you can't have multiple interface IP addresses in the same subnet.

---

### Post by risva on 2015-07-07
@BAB1,

I get your point,..... i would like to make a correction!

My requirement is not to route but to carry out L3 switching along with firewall functionality. There would be no WAN involved. 

The /24 LAN IPs is what i get from my regional office. I have to distribute them to different sections in my office. /27 has been chosen based on functional requirement, IPs left over can be used later for different requirements. 

Also, the rules that I have listed are only example set.... i intended modifying exact rules later on.

---

### Post by bab1 on 2015-07-07
> **risva said:**
> @BAB1,

I get your point,..... i would like to make a correction!

My requirement is not to route but to carry out L3 switching along with firewall functionality. There would be no WAN involved. 

The /24 LAN IPs is what i get from my regional office. I have to distribute them to different sections in my office. /27 has been chosen based on functional requirement, IPs left over can be used later for different requirements. 

Also, the rules that I have listed are only example set.... i intended modifying exact rules later on.L3 Switching is routing in hardware as I see it.  An Ubuntu host is an all software router (for L3).  So I'm still a bit confused on what you want to do.  Are you using the Ubuntu host to route and L2 switches to distribute the traffic to the client hosts.  Are all the hosts in the same physical location?  

The reason for my questions is this statement by you> ... IPs left over can be used later for different requirements....not if you want to add them to the subnets you created.  The boundaries are numerically fixed.  If you intend on adding or subtracting hosts to these subnets then you should use VLANs rather than true subnets.

The firewall rules are vague at best right now.  The subnets or VLANs should be created in a testing situation first.

---

### Post by risva on 2015-07-07
The answer to first question is yes!!, ubuntu host to route and L2 sw to distribute. different NIC interfaces, in ubuntu host, defined for different subnets will be connected to different L2 switches and the PCs of various subnets will be connected to respective switches.

Your concern regarding subnet defining is understood, believe me.... i should be able to take care of them.

I need help in configuring ubuntu for this routing to take place and also for implementing example firewall rules...

---

### Post by bab1 on 2015-07-07
> **risva said:**
> The answer to first question is yes!!, ubuntu host to route and L2 sw to distribute. different NIC interfaces, in ubuntu host, defined for different subnets will be connected to different L2 switches and the PCs of various subnets will be connected to respective switches.

Your concern regarding subnet defining is understood, believe me.... i should be able to take care of them.

I need help in configuring ubuntu for this routing to take place and also for implementing example firewall rules...
here are the rudimentary steps:
[LIST]
[*]Set the forwarding on in the kernel
[*]use IPTables to forward specific interfaces to and from specific interfaces
[*]
[/LIST]

See [here]("http://askubuntu.com/questions/95199/two-network-cards-and-ip-forwarding") for a starter on how to do it with Ubuntu.  Why no specifics?  Because I don't do that sort of thing.  I use a dedicated router or L3 switch to do that sort of thing.  I answered because of your incorrect subnetting.

---

### Post by risva on 2015-07-07
thanks BAB1

---

