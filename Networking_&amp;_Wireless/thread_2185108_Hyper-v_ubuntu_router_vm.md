---
title: "Hyper-v ubuntu router vm"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by actingrude on 2013-11-01
I am afraid this may be beyond the scope of these perticular forums but I figure if I cast as wide a net as possible I have a better chance at catching an answer.

I am running hyper-v on a 2012 windows server with many ubuntu and other os vm servers. This is just a lab setting at the moment as I am preparing it for a future applications, but here it is.
I am attempting to use one of the vm's as a "router" to provide internet access to the other vm's and to a switch (and many other clients through the switch). I have found a bit of information on setting up this "router" with bridges and port forwarding in the ip-tables but I am struggling to get it to actually work in my setting.
on hyper-v I have 3 virtual switches set up;
 one that connects to the modem using a card I will call eth0, it is an external virtual switch
one that is internal that has all of the vm's attached to it (and just it, with the exception being the "router vm") eth1
one that is external that connects to the switch that SHOULD provide internet to all of the other computers on the network (eth2).

I have attempted to bridge the connection from eth0 to both eth1 and eth2. Now I have tried this a few different ways so far with no success.
Can anyone point me in the right direction so far for what I may be doing wrong and if this is possible without a lot more work?
also, am I right in assuming that once the bridge is set up, using any of the many different ip-table configurations I have found shouldn't be necessary to just get internet access on the other vm's and the network behind the switch?
Thank you so much for any help, and if this is better placed in a different sub-forum I apologize.

---

