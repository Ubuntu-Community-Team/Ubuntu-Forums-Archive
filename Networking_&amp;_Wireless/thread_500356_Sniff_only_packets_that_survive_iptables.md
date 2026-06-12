---
title: "Sniff only packets that survive iptables"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-07-13
I'm currently using iptables to manage my firewall. When I start a packet sniffer, it sniffs all packets coming in and out of my machine, including packets that are being stopped at the firewall by iptables.

Since iptables manipulates how packets are handled by the kernel, is it possible to somehow only sniff packets that have already passed through the kernel? I want to be able to only see packets that have successfully made it through the firewall.

---

### Post by B-Con on 2007-09-19
(Bump.)

Any ideas of how to do this? Might I be able to create a virtual loopback device or something and route one network device to just stream into the other (if the kernel kills the packets, I'm assuming that it would pick off the packets between device A and device B)?

I have a firewall that seems to be flaking out on me, and it would be really helpful in debugging my iptables rules if I could figure out which packets are being rejected and which are being accepted.

---

