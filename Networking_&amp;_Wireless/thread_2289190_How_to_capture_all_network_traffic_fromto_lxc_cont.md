---
title: "How to capture all network traffic from/to lxc container"
date: 2015-08-02
forum: Networking &amp; Wireless
---

### Post by Jim_Lynch on 2015-08-02
This is a two part question.  The first question is "What device should I be using to capture LXC destined traffic on the host?".  I'm pretty sure all traffic is routing through the br0 device but from an efficiency standpoint, it makes sense not use that one.  I have br0, eth0, lo, lxcbr0, vethEIRGJU.  Logically it looks like lxcbr0 might be the one.  It doesn't seem to capture anything useful.  I then tried to use br0 and look at all traffic to/from the container.  Nope, that only captures data from the host to/from the container.  What I really need is what's going on between the container and the WAN.  

Any ideas?

Thanks,
Jim

---

