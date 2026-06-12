---
title: "multi homing"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by mudcow007 on 2007-11-08
hello all 

is it possible to run two seperate network cards as one in the same machine?

basically we have a ubuntu feisty server with Asterisk pbx software running on it. 

The card is running at between 80 - 100% usage. Im sure i have seen it soemwhere, were you can share the load between two cards?

is it possible?

thanks

**edit** sorry i forgot to mention i would like the two cards to have the same IP (i know this may cause conflicts!). this is because of the set up of Asterisk

---

### Post by netztier on 2007-11-08
> **mudcow007 said:**
> 

**edit** sorry i forgot to mention i would like the two cards to have the same IP (i know this may cause conflicts!). this is because of the set up of Asterisk

Nah, it won't cause conflicts if you configure **bonding **. This will generate a virtual interface (most often conveniently called bond0) that will have the IP address, Subnet mask and other ip parameters. eth0 and eth1 (assuming they're called like that) will be "enslaved" to bond0.

About bonding: [http://ubuntuforums.org/showthread.php?t=283113&highlight=bond](http://ubuntuforums.org/showthread.php?t=283113&highlight=bond)

But things are not THAT easy. To be truly effective, the bonding configuration has to take into account the traffic/load patterns, especially how many different MAC addresses your system is talking to (check the ARP cache). Traffic distribution in a bond is mainly done based on MAC addresses.

[LIST]
[*]Is the high load your system is experiencing *incoming* or *outgoing*?
[*]Does this interface communicate with a lot of different peers? 
[*]Are they all on the same IP subnet as the server? (so you'd see communications with a lot of different MAC addresses and a large ARP cache)
[*]Are the peers on different IP subnets and do they reach the server via a router? (so you'd see communications with basically just the single router's MAC address - and not many entries in the ARP cache)
[*]If yes, is there more than one router on the server's subnet? (so you'd see communication with the MAC addresses of the 2 or more)
[/LIST]

For some modes of bonding (actually, the most common one with LACP), both (or all) NICs used for the bond must be connected to the same LAN switch, and this switch must support LACP, too.

best regards

Marc

---

### Post by mudcow007 on 2007-11-08
thanks for your reply netztier

im looking into it now :)

---

### Post by timcredible on 2007-11-08
can you upgrade your nic to a higher speed nic?

---

### Post by mudcow007 on 2007-11-08
hi Tim

the nic is 1000Mb

---

### Post by netztier on 2007-11-08
> **mudcow007 said:**
> hi Tim

the nic is 1000Mb

Ehm? 

And yo're getting 800Mbps, from Asterisk traffic alone? What kind of MONSTER PBX system is this?

Are you shure the card is actually running at 1000Mbps?

best regards

Marc

---

