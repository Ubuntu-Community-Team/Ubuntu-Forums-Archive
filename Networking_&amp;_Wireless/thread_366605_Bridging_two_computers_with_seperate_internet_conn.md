---
title: "Bridging two computers with seperate internet connections"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by austin987 on 2007-02-21
Howdy,

I live in a dorm room, and have two ethernet ports, only one of which is being used. I'd like to hook up the 2 main computers to their own 10 Mbit connection, and then run a crossover cable across the 1Gbit connections each has to share files between them. Is this possible?
Diagram:

Internet -----10Mbit---------- > Computer 1 (Running Dapper/XP)
                                                     |
                                         Network Bridge 1 Gbit crossover cable
                                                     |
Internet -----10Mbit----------  > Computer 2 (Running Dapper)

I can setup each with their own connections/static IP's/etc. As for the bridge, would it be a matter of setting up a different IP range/subnet on each computer for those two ports, then setting the IP of the other computer in the hosts file? How can I force each computer to carry network connections for the other computer across the private network rather than over the internet. Is it possible then to have the internet be a failsafe option, if the other cable is unplugged?

Thanks for the help!

---

### Post by spd106 on 2007-02-21
I think you have the right idea.

It's normal to put the private network in the 192.168.0.0 - 192.168.0.255 range, (with a subnet mask of 255.255.255.0 == /24). So as an example, put one on 192.168.0.1/24 and the other on 192.168.0.2/24

Put the details in the /etc/network/interfaces file or you can use the network-admin capplet.

Yes, editing the /etc/hosts file will allow name resolution to work easier.

There should be a route to the other PC automatically generated, if this doesn't happen then you can add it manually with say *sudo ip route add to 192.168.0.0/24 via 192.168.0.1 dev eth1*.

Both PCs will have an external network viewable address, you should be able to see it with ifconfig and be able to ping each other. If so, file sharing should be possible, just remember that the external network is not necessarily secure.

---

