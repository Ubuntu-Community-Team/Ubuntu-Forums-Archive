---
title: "Socat broadcast"
date: 2020-12-11
forum: Networking &amp; Wireless
---

### Post by rparadam on 2020-12-11
Hi,

This command allows to forward incoming UDP packets from port 8947 to a given machine `sudo socat UDP4-RECVFROM:8947,fork UDP4-SENDTO:192.168.1.63:8947`. Although it works for a single machine, I would like to transmit it broadcast. I've tried 192.168.1.255, .0  and 0.0.0.0.  Is there any solution using socat?

---

