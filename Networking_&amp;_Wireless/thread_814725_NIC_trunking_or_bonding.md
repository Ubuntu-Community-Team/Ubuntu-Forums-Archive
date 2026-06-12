---
title: "NIC trunking or bonding"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by zugg on 2008-06-01
I'm fairly new to this level of systems management....

I've just got a file server with 4 gigabit NIC's (two on motherboard, two on a separate card) raid 6 on 16 drives, etc.  we have a large cpu render farm that hammers the server constantly with large loads both read/write.  I would like to bond/trunk the 4 gigE ports on the server so i can get 4 gigabit transfer to/from the file server.

I have a 48 port gigE switch that i can (easily, it seems) link aggregate 4 ports together, so that leaves me with properly setting up the file server to bond it's 4 ports together.

i honestly don't really know where to start.  i'm running ubuntu 8.04 server edition.  i've read a few other posts on the forums but haven't found anything that truly matches my situation.

any help very much appreciated!

.z

---

### Post by pdwerryhouse on 2008-06-01
You'll want the *ifenslave* package.

The kernel module that is needed for this is bonding.o. I think you'll want bonding mode 4 (802.3ad, aggregation). So:

modprobe bonding mode=4 max_bonds=1

ifconfig bond0 {... blah blah ... } up
ifenslave bond0 eth0
ifenslave bond0 eth1
ifenslave bond0 eth2
ifenslave bond0 eth3

And voila. I hope. I've only ever used bonding for high-availability failover, not aggregation.

Further docs are here: [http://www.kernel.org/pub/linux/kernel/people/marcelo/linux-2.4/Documentation/networking/bonding.txt]("http://www.kernel.org/pub/linux/kernel/people/marcelo/linux-2.4/Documentation/networking/bonding.txt")

---

