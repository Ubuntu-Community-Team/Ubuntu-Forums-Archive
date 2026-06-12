---
title: "Duplicate IP"
date: 2016-11-23
forum: Networking &amp; Wireless
---

### Post by mansooralikodakkadan on 2016-11-23
My company network is very unstable. It takes so much time to ping to gateway about 50ms or higher. I did some troubleshoot to find out the cause. I have to try arp-scan when network is unstable and see many duplicate IP with same MAC address. This is a section of output:

  I ran an arp-scan to detect any ip address conflict in the network. The output as seen below:

```
192.168.x.91     02:a0:xx:xx:d6:64        (Unknown)

192.168.x.91     02:a0:xx:xx:d6:64        (Unknown)  (DUP: 2)

```
  Please note the (DUP :2)

  What does the o/p describes, showing duplicate for same ip and mac address. How can that be a duplicate?

---

### Post by HermanAB on 2016-11-23
Some cheap skate manufacturers re-use MAC addresses, which can cause these issues.

You got to track the offending hardware down and toss it in the bin.

---

### Post by howefield on 2016-11-23
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by The Cog on 2016-11-23
Given the duplicate MAC addresses,I think the most likely explanation is that the network is somehow duplicating packets. I have read that this can happen in wifi connected networks, and I think it can happen occasionally in switched networks. 

A full-on bridging loop (e.g. two switches connected by two separate cables, forming a circular path) can happen under some circumstances. For instance, an error in the spanning-tree protocol that is intended to prevent such loops by auto-disabling one port in the loop.  But the packet repeat storm in that case is so severe that it normally kills the connectivity completely. Although this might fit your description of the symptoms, I would expect very many repeats in that case, not just the occasional one. Running tcpdump during the problem period would show a massive stream of broadcast packets if this were the problem.

---

