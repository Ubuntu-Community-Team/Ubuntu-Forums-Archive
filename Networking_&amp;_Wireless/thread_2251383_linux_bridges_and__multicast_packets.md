---
title: "linux bridges and  multicast packets"
date: 2014-11-04
forum: Networking &amp; Wireless
---

### Post by c-vijaya-durga on 2014-11-04
hello all,

I am pretty new to linux networking and linux in general. I am trying to put up a virtualised network on  ubuntu 12.04LTS VM.
As of now,I could create containers (lxc-create -t ubuntu -n <name> ), get LXC containers working and am running a routing engine on each of the container . Thus each container is now functional as a virtual router.
Both the containers have the lxcbr0 as default gateway (10.0.3.1)
I can ping container1 to container2 and vice versa, but am unable to run any routing protocols.
with the help of wireshark, I could figure out that the routing multicast packets from container1 and container2 are reaching the bridge and nothing seems to be happening from there on. I am not too sure, but looks like the linux bridge lxcbr0 is not forwarding the multicast packets. This is a little confusing to me as I thought linux bridges work like hardware switches and thus both container1 and container2 are on same LAN.

How can I get the bridge to do multicasting?

IP details are attached.
[ATTACH=CONFIG]257732[/ATTACH]

[ATTACH=CONFIG]257731[/ATTACH]

---

### Post by bashiergui on 2014-11-08
What are the IPs of the containers? What multicasting address are you using? Have you enabled multicasting /icmp on the bridge?

---

### Post by bapoumba on 2014-11-08
*Thread moved to **Networking & Wireless**.*

---

