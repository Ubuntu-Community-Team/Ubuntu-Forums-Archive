---
title: "Netmask networking question"
date: 2014-03-25
forum: Networking &amp; Wireless
---

### Post by cherva on 2014-03-25
If I have 1 network that is currently 192.168.0.X with netmask 255.255.255.0.
And I create a second network for VMs only 192.168.1.X, I will need a machine to NAT all the 192.168.1.X traffic to and from the 192.168.0.1 gateway. ( this is needed in order to preserve the 192.168.0.1 network from crashing if someone, somehow crashes the 192.168.1.0)
I'm ok with that, but my question is:
After I'm satisfied with the VM tests can I just lower the netmask of the 192.168.1.X network to something like 255.255.254.0 to eliminate the need of the NATing machine and to ease the access to the VMs from the 192.168.0.X network.

---

### Post by TheFu on 2014-03-25
Netmasks are about pure ethernet connections - that means they can find each other without a router by pure ethernet addressing using MAC addresses.   Also - every machine would need to have the same netmask.  So, I have doubts that is possible if there is a routing machine in the middle, but try it during a maintenance window and let us know.

OTOH, I'm not sure what having a larger netmask actually gets you in this specific configuration - the VM host will still need to route anyway.

---

### Post by cherva on 2014-03-25
Theoretically if the 192.168.0.X machines have 255.255.254.0 as netmask and the 192.168.1.X machines have the same netmask with GW 192.168.0.1 it should work as expected.
The 192.168.1.X VMs will have internet and the users on 192.168.0.1 will be able to access the VMs directly.
Or I'm wrong ?

---

