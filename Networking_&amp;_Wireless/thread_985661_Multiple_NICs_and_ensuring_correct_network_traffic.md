---
title: "Multiple NICs and ensuring correct network traffic flow"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by Pixelmilitant on 2008-11-17
Hi all,

I'm currently in the process of building a game server on top of ubuntu server 8.10, and I've recently installed 2 extra NICs, giving me 3 network interfaces.

I've given static addresses to each, but I've noticed some strange behaviour.

This is how my interfaces are set up:
eth0 = x.x.x.150
eth1 = x.x.x.151
eth2 = x.x.x.152

For example, if I bind a teamspeak server to eth1, and then type 'ifdown eth0', the teamspeak connection dies. Likewise when i ping eth1 or 2, and then drop eth0, the ping dies.

I was under the impression that network traffic would find the correct NIC and avoid using the others, but it seems thats not the case.

If anyone has any pointers, I'd love to hear.


Thanks,
Pixmil

---

### Post by Pixelmilitant on 2008-11-18
Just a thought,

If I altered the firewall to only allow specific applications to specific IP addresses (such as port 80 to x.x.x.150, port 27015 to x.x.x.151, etc), then will that minimise interface traffic?

Basically, I don't want to run a game server on eth1 (x.x.x.151), only to have it route its way through eth0 first.

---

### Post by forbjok on 2008-11-18
Are the 3 IPs using the same subnet, or different subnets?

For example with 24-bit subnet (255.255.255.0):
192.168.1.150-152 (same subnet)

or

192.168.1.150
192.168.2.151
192.168.3.152

If all 3 NICs are using IPs on the same subnet, then the routing table will get confused about which interface the subnet should be routed through, and probably just settle on one. (possibly the first - I'm not exactly sure how the system would behave in such a case)

If so, then you should just use 1 NIC instead. Just set all 3 IPs on a single NIC to avoid any problems.

Or alternately use different subnets for the 3 interfaces.

---

### Post by Pixelmilitant on 2008-11-18
Hi forbjok,

The interfaces are as following:

eth0 - 192.168.1.150
eth1 - 192.168.1.151
eth2 - 192.168.1.152

I was not aware that there would be an issue of having the 3 NICs on the same subnet, in the same computer. I assumed they would act like separate clients on the network, and that it was up to me to decide which services go where.

I've also tried network bonding, but it seems that my network cards (cheap realteks) do not support bonding.

So, do I just go back to 1 NIC and hope that i don't experience slowdowns?

Just for context sake, the purpose of this server is to host a LAN party, so it will be performing DNS, DHCP, file serving, and game hosting tasks. My biggest concern is game latency, especially when people start downloading big patches and game clients from the same interface....

---

### Post by superprash2003 on 2008-11-18
by default.. when there are 3 connections to the internet or network.. the computer uses the fastest..

---

### Post by forbjok on 2008-11-18
> **Pixelmilitant said:**
> Hi forbjok,

The interfaces are as following:

eth0 - 192.168.1.150
eth1 - 192.168.1.151
eth2 - 192.168.1.152

I was not aware that there would be an issue of having the 3 NICs on the same subnet, in the same computer. I assumed they would act like separate clients on the network, and that it was up to me to decide which services go where.

I've also tried network bonding, but it seems that my network cards (cheap realteks) do not support bonding.

So, do I just go back to 1 NIC and hope that i don't experience slowdowns?

Just for context sake, the purpose of this server is to host a LAN party, so it will be performing DNS, DHCP, file serving, and game hosting tasks. My biggest concern is game latency, especially when people start downloading big patches and game clients from the same interface....

It might be better to go with a single Gigabit Ethernet controller instead of 3 100Mbit ones.

Or at least use non-Realtek ones.
I've got quite a few realtek-based network cards myself, and while I've never had any serious problems with them, they are not really known for their efficiency.

Intel Ethernet adapters are high quality, although they are somewhat more expensive than Realtek-based cards.

---

### Post by Pixelmilitant on 2008-11-18
Hi forbjok,

I appreciate and totally agree with the advice.

I'd rather pay money for decent hardware than to have 50 gamers after my blood!!

I've got an Intel PRO 1000 MT on order, and I will go from there.


As far as the topic of multiple NICs in one PC/one subnet is concerned, is it possible to carry on the conversation as to if/why it is impossible to do? Just from a technical perspective.


Thanks again,
Pixmil

---

### Post by dmcbob on 2008-11-19
I have a similar issue with 2 NICs on a computer (COMPUTER2 below) - whenever I enable both it tries to reach the internet via the faster one (which is also only collected to a local subnet without internet access). Is there anything I can do?

My setup is as follows:
COMPUTER1 ---- router1 with DHCP enabled ---- COMPUTER2 ------wireless router2 to the internet with DHCP

Router1 is 192.168.0.1, while router2 is 192.168.1.1. I haven't changed the subnet masks, so they're both 255.255.255.0. Is there a way to tell my computer to use subnet2?

Thanks for any help.

PS: It's okay for now that COMPUTER1 has no internet access. I'm not trying to solve that at the moment...it's just there to back up info on COMPUTER2.

---

### Post by forbjok on 2008-12-23
> **Pixelmilitant said:**
> Hi forbjok,

I appreciate and totally agree with the advice.

I'd rather pay money for decent hardware than to have 50 gamers after my blood!!

I've got an Intel PRO 1000 MT on order, and I will go from there.


As far as the topic of multiple NICs in one PC/one subnet is concerned, is it possible to carry on the conversation as to if/why it is impossible to do? Just from a technical perspective.


Thanks again,
Pixmil

The reason it's not a good idea to have multiple NICs with IPs in the same subnet is the routing table.

In order to know which physical NIC packets destined for a particular IP needs to be sent to, it uses the routing table, where it has stored a list of existing IP subnets, and which physical NIC they belong to. If an IP doesn't match any of the subnets on the local interfaces, it will be passed on to the default gateway, which is the route with subnet 0.0.0.0/0.

If 2 NICs have IPs in the same subnet, the OS will get confused about where it's supposed to send the packets.

To make an example, let's say you're driving along a road, and know the name of the place you're going to, but not the exact route to get there. Then you get to a crossroads, and there are 2 signs, both with the name of the place written on them, but pointing in opposite directions. How would you know which one is right?

---

### Post by natrab on 2009-02-08
Ok, I'm bumping this thread as it affects me (keep in mind I'm a linux noob).

I have a server hosted on a home fiber line with dual NICs.  Now I have two static IPs on the same subnet, each of which are assigned to a different NIC card.  Unfortunately this is the only way I know of to do it as my ISP assigns static IPs based on which MAC address is searching for one.

Now I'd have no problem using a single NIC if I could, but I'd need a way to create a second "virtual" mac address to pull a second IP for the adapter.

Otherwise, I need to find a way to get both IPs working on the same machine using two separate NICs and two separate IPs.

Right now if I restart the server, one of the IPs will work.  I then have to go in there and add a route to whatever adapter isn't working to the default gateway and they both work.  I just want this to work automatically (it won't save two default gateway routes for some reason).

Thanks in advance for the help.

---

