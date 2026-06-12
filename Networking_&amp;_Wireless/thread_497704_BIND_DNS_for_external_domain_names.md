---
title: "BIND DNS for external domain names"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by SuperJason on 2007-07-10
Sorry if this isn't specific to Ubuntu.  It's really more of a BIND question, but you guys are helpful.

I successfully configured BIND for my local network, and it runs great.  Is there is a way to override a couple of select domains in an easy way?

For example, I want to override [www.google.com](www.google.com) to point to a certain IP address (that's just an example, maybe not a good one).  I can set up zones for each domain, but that is a lot of work.  I would rather just have some kind of generic zone where I can define them.  Kind of like a "hosts" file.

Extended Explanation (no necessary to read): I have some external domain names that ultimately point to computers in my network.  If a computer is plugged into the network, I want to avoid routing it outside the network.  Only external machines will be going through the external address.

---

