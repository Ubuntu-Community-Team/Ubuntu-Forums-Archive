---
title: "simulating poor WAN connection"
date: 2022-03-25
forum: Networking &amp; Wireless
---

### Post by mkeating on 2022-03-25
I want to simulate a poor WAN connection for testing the minimum speed/latency a particular network can function with.   I think I can use Netem and set up an Ubuntu machine as transparent  bridge to accomplish this.  I don't have any spare hardware with two rj45 ports at the moment to test with.  I've tired using the Netem commands to transfer files on a local network, which seems promising.   I don't know if I'm going to get fouled up with vlan tags or something.

Thinking it would go here:
switch-----------Firewall----[Ubuntu_bridge]------Router-----


Can someone tell me if what I'm thinking is feasible?

---

### Post by Andrew_Welham on 2022-03-31
have you tried with a VM, then you can use software configures NICs.
I've done something similar in the past to simulate latency. Just cant remember the s/w used.

---

