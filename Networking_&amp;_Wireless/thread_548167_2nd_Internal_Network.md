---
title: "2nd Internal Network"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by dualusbibook on 2007-09-10
I have been trying to find out some information on setting up a second IP address for my ubuntu system.  I have been able to find bits and pieces on the forum and google but still have a few questions.

I have two static IP address both are working without any problems on (Machine A) and (Machine B).

(Machine A) is also acting as a router for my internal network with an IP address of 10.0.0.1.

My goal is [if possible] is to add (Machine B) to my internal network so I can back up my files to a third computer that is at 10.0.0.8.  The reason for this is I do not want to use up additional bandwith from my ISP if I can help it.

The command that I have found which appears to work is:

ifconfig eth0 add 10.0.0.100 netmask 255.255.255.0

From (Machine C) I am able to log into (Machine B).

The questions I have are:
1) Is this possible?  Without the changes I know the network is working fine as it has been this way for a few years.  I don't want to start causing problems as I host a few websites on (Machine B).

2) I have also been reading about the command "route".  Do I also need to add a route on (Machine B) to use the router IP address of 10.0.0.1 in addition to my ISP's?

3) If I leave just the above ifconfig command will it cause any network problems with external traffic talking with my static IP address?

(Machine A) is a vintage Mac running IPNetConfig.  A solid performer for the last decade.
(Machine B) is running Ubuntu Server 6.06 (PPC)
(Machine C) is running Mac OS X

Any useful websites are also appreciated.

Cheers

---

### Post by rivalarrival on 2007-09-11
You need to better describe your network setup... How many NICs in each machine, and to what are they physically connected? Are you using separate equipment for your external and internal network, or have you somehow managed to get both your external and your internal subnet running on the same physical network?

If you're not trying to run multiple subnets on the same physical network, it's simply a matter of having two nics in machine B, connecting the second to your internal network's equipment, setting it's ip address and subnet mask, but not assigning a gateway (It shouldn't need one on the internal side as all traffic should be in the same subnet)

---

### Post by dualusbibook on 2007-09-15
Hi rivalarrival,
I will try to elaborate on my network setup.

I have the one physical line coming from my ISP.  This goes directly into my switch.  Also connected to the switch are all my other systems (wired and wireless).

Computer A has 1 NIC.  The machine itself is plugged into the switch and assigned the external IP address that is on the subnet 255.255.248.0.  Through the program IPNetRouter (software router) I am able to use IP masquerading to create a 255.255.255.0 subnet that allows all my computers to connect to the internet using this computer as the router.  I use 10.0.0.1 for the router and assign static IPs for the rest of the internal IPs.

Computer B also has 1 NIC card.  It is plugged into the switch and uses the IP address supplied from my ISP.  The subnet I have it using is 255.255.248.0 as well.

All my other systems are using the subnet 255.255.255.0 with an IP address based on the 10.0.0.1 router.

To reiterate what my goal is I would like to have Computer B also get an IP address from my software router that could be accessed locally instead of using my bandwidth.

I hope this provides enough detail.  If can try to clear up anything if it is not clear.

---

### Post by dualusbibook on 2007-09-28
I have done a bit more reading this evening and I have found the command:

ifconfig eth0:0 10.0.0.100 netmask 255.255.255.0 up

This provides a route table of:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0    *               255.255.255.0   U     0      0        0 eth0
172.172.1.0   *               255.255.248.0   U     0      0        0 eth0
default         172.172.1.1   0.0.0.0         UG    0      0        0 eth0

This appears to be working correctly now.

Would this be the ideal setup or is there a better method of still having the setup I want.

Thx

---

