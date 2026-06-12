---
title: "[SOLVED] Networking using a switch"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by kevinlyfellow on 2007-06-21
I'm learning how to network and I've successfully figured out how to network two computers directly (a small step, but hooray! anyways).  I'll be adding several more computers and will be using a switch.  My first assumption was that I could just plug the eth cables into the switch and it would work, but apparently I'm wrong.  I've basically set up the ip-addresses and subnet mask in /etc/network/interfaces  What do I need to do to get this two computer setup using a switch?

Any resources that you think may be helpful would be appreciated.

---

### Post by Mr. C. on 2007-06-21
Each Ethernet device needs its own unique IP address.  A switch works at a lower layer, so does not get involved with IP address allocation.

You will need to statically assign unique IPs to each system, all on the same subnet, same subnet mask.

Good for you for taking one step at a time, and building a solid foundation.

Spend a little time going through the networking notes and labs at :

[http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

---

### Post by kevinlyfellow on 2007-06-21
Thanks Mr. C, enjoying the course notes (I'm sure your students aren't as excited ;-))

> all on the same subnet

When you say "all on the same subnet", do you just mean physically on the same subnet (I'm new to all of this, so I'm a bit cautious with the jargon)?  In order to create a new subnet I'd need to have another switch correct?

> You will need to statically assign unique IPs to each system, all on the same subnet, same subnet mask.

It seems like the configuration of two computers on a switch are the same as connecting two computers directly through their nics.  The switch is just there to allow the connections to take place?

---

### Post by coolguy2006delhi on 2007-06-21
Well , let's first understand why static ip is requires. When there are handful of computers , you can assign the ip addresses ti individual computers manually. This is called static ip address. But suppose you have 1000 computers, it is just impossible task to manually assign ip address to all the machines. Therefore we use DHCP server that assigns ip address to all the machines on the network. Now about the subnet. Among 100 computers , 50 belong to suppose dept A and other 50 belong to dept B. To distinguish between them, we use subnet mask. In other words you can say that you assign max number of nodes in a particular network of same purpose.A switch just act as connector of several computers.A hub also do the same job.

---

### Post by Mr. C. on 2007-06-21
kevinlyfellow,

The distinction between physical network and subnet is difficult for beginners to grasp, because the definition of subnet involves a concept of "broadcast domain".  But lets ignore that for the moment.

In your case, subnet means the network as defined by the network mask (aka: subnet mask, netmask). This value is what splits the network portion of the IP address from the host portion.  ( This is shown in the class notes .)

The ports on a switch (and a hub for that matter) connect hardware in the same broadcast domain.  This means, they have the same subnet mask.

Each layer 3 piece of Ethernet hardware (this include NICs, routers) requires correctly configured IP information in order to successfully communicate.   *How* that IP information is assigned is only a matter of admin convenience, the typical options being static, dynamic (DHCP/BOOTP), and automatic.

Connecting two computers via (crossover) ethernet cable has the same requirements: IP information must be configured.  In this case, systems can provide automatic IP configuration, so that no admin is required. Or, one system may provide IP information via a DHCP running on one of the systems.  If neither is available, you will need to manually configure the IP information (aka: static).

The rules do not change when using a swtich to interconnect two or more pieces of hardware. IP information must be configured.  The switch does not produce multiple networks; all hardware connected to the switch is on the same network (aka: subnet).

Its best to first pick the IP address of the network, as in:

   192.168.4.0 / 24

This corresponds to a network mask of:

   255.255.255.0

and a broadcast address of 

   192.168.4.255

Now, you can assign IP addresses to each host:

   192.168.4.10
   192.168.4.19
   192.168.4.202

Note that each interface has the 192.168.4 network part.  This is because we used 24 bits for the network part, and 8 bits for the host part.  Only hosts 0-255 are possible in a /24 network split.

The notes should clear up additional details, or feel free to ask more questions.

MrC

---

### Post by linuxonbute on 2007-06-22
Also you need to remember that the cable you use to directly connect 2 computers together is called a crossover cable. If you connect using a switch or hub each must have a straight cable. The crossover cable will not work.

---

### Post by kevinlyfellow on 2007-06-22
> **linuxonbute said:**
> Also you need to remember that the cable you use to directly connect 2 computers together is called a crossover cable. If you connect using a switch or hub each must have a straight cable. The crossover cable will not work.

Well, the cable is being crimped by hand.  I successfully got two computers to directly connect, so I must have crimped a crossover cable?  That must be why it didn't work on the switch.  Oops... :-\"

---

### Post by Mr. C. on 2007-06-22
Newer Ethernet devices are coming with auto-mdx, which detects the correct tx/rx pairs automatically.  Crossover cables will be a thing of the past.  You may have such a device.

Ethernet cables (esp. at 100mb and greater) have very strict requirements for proper operation.  For example, if the cables untwist length is greater than about 1/2" at the connector, performance will suffer due to excessive errors.  Be sure to maintain very strict conformance to the specs for maximum throughput and proper operation.

MrC

---

### Post by linuxonbute on 2007-06-23
The cable is 4 pairs of wires. each pair being twisted together.

Straight cable is  1-1   2-2  3-3  4-4  5-5  6-6  7-7  8-8
but crossover is  1-3  2-6  3-1  4-4  5-5  6-2  7-7  8-8

4,5,7,8 are not used for this type.

---

### Post by kevinlyfellow on 2007-06-23
> **linuxonbute said:**
> The cable is 4 pairs of wires. each pair being twisted together.

Straight cable is  1-1   2-2  3-3  4-4  5-5  6-6  7-7  8-8
but crossover is  1-3  2-6  3-1  4-4  5-5  6-2  7-7  8-8

4,5,7,8 are not used for this type.

Thanks, I think what happened was that I followed the guide that came with the crimping kit, but I used a cable with one end that a manufacture had made.  I didn't bother to check to see if the were the same setup :-/

---

### Post by kevinlyfellow on 2007-06-25
Ok, I've check the cables, they are straight... I'm confused, why would this work???  Everywhere is telling me I need crossover, but that is NOT what I have!  Any ideas?

---

### Post by Mr. C. on 2007-06-25
I gave the answer earlier:

[quote=MrC]Newer Ethernet devices are coming with auto-mdx, which detects the correct tx/rx pairs automatically. Crossover cables will be a thing of the past. You may have such a device.[/quote]

MrC

---

### Post by kevinlyfellow on 2007-06-25
> **Mr. C. said:**
> I gave the answer earlier:



MrC

Sorry, my eyes glazed over because I didn't know what auto-mdx or tx/rx meant :-/  thanks :-)

---

