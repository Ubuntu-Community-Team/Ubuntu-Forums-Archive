---
title: "Redirecting traffic to eth0/eth1"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by Kartik Babu on 2006-11-07
this is a network programming question.

I would like to send a packet, for now lets say a ping packet through a specific interface. I know that the ping program supports this. What I want to know is how to set it up in my own source code, so that I can send a packet through eth0 or eth1 depending on what my code chooses.

Do I set it up at the socket level, or when I'm assembling the packet header?

Currently I'm at a loss to find source code samples on the net.

Any help is appreciated, thanks.

---

### Post by GorBo on 2006-11-07
> **Kartik Babu said:**
> What I want to know is how to set it up in my own source code, so that I can send a packet through eth0 or eth1 depending on what my code chooses.

After you create a socket, you can use setsockopt to bind it to a specific interface. See man pages socket(7) and setsockopt(2).

---

