---
title: "Real performance figures for 10-gigabit ethernet?"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by 1clue on 2014-01-31
Hi,

I'm contemplating going to 10gbE for a few servers.

I'm setting up a couple VM hosts, probably based on qemu.  one gigabit is pretty slow for some things I'm doing on my network, and I'm hoping to get real performance figures and maybe some tips on 10gbE before I go waste a bunch of money.

I'd like real figures on just pure host-to-host networking, and also if somebody has figures for virtualization-aware cards like SR-IOV, all I can find comes from the manufacturer so I don't know how it works on a real network.

At the moment I see 3 devices:  2 vm hosts and 1 storage device.  At first I may try to go peer-to-peer on this.

Thanks.

---

### Post by tgalati4 on 2014-02-01
10 to 1 is a rule of thumb that I use.  A 10-gigabit bandwidth will comfortably give you 1-gigabit per second throughput.  The ratings are peak.  The nature of the traffic collisions and supporting multiple devices with radios all squawking at once limits your actual, sustained throughput to about 1/10 of the peak.  With point-to-point and no other devices on the network, you can sometimes get 1/2 of the peak speed.

You can perform some benchmarks with *iperf*.  Let us know what you find.

---

