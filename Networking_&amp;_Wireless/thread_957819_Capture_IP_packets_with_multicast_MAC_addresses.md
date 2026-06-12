---
title: "Capture IP packets with multicast MAC addresses"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by arrowheart on 2008-10-24
I disable ARP service on all involved hosts, set up a static ARP table where a unicast IP (destination) address is mapped to a multicast MAC address.

Then I deploy RAW sockets on a sender and a number of "virtual" recipients. The sender thought it was talking to a single recipient (in IP layer).But actually the outgoing packet is wrapped in an Ethernet frame with multicast MAC address. By Wireshark, I know that all hosts on the LAN receives the frame. But the recipients' program cannot get the IP packet. Does it mean, only if the destination IP address matches the recipient's IP address, the kernel will deliver it to my program?

Thanks

---

