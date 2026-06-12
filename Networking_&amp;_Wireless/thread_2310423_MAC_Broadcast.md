---
title: "MAC Broadcast"
date: 2016-01-19
forum: Networking &amp; Wireless
---

### Post by May_Masters on 2016-01-19
Hi all,

I'm gonna setup one of our routers with a MAC Filter. Now I was told that I must not restrict MAC: FF:FF:FF:FF:FF:FF as this is the Broadcast address.
But I've never seen a Layer 2 (Link) Broadcast only Layer 3 (Network).

What would happen if I block this MAC ? (Isn't that a potential "foot in the door" to start a DOS attack by flooding the network with requests ?) 
DHCP is on, so will it still work ? (DHCP Server is in the Router - hence it's the same Segment)

---

### Post by bab1 on 2016-01-19
> **May_Masters said:**
> Hi all,

I'm gonna setup one of our routers with a MAC Filter. Now I was told that I must not restrict MAC: FF:FF:FF:FF:FF:FF as this is the Broadcast address.
But I've never seen a Layer 2 (Link) Broadcast only Layer 3 (Network).

What would happen if I block this MAC ? (Isn't that a potential "foot in the door" to start a DOS attack by flooding the network with requests ?) 
DHCP is on, so will it still work ? (DHCP Server is in the Router - hence it's the same Segment)
If you restrict the MAC: FF:FF:FF:FF:FF:FF then ARP won't work properly.  When the ARP protocol asks "who has this IP address?" it is using MAC broadcast to talk to all hosts on the local network.

What is the purpose of the MAC filter anyway?

---

### Post by May_Masters on 2016-01-20
aha, ok, I understand.

Well, I've to restrict certain PS/Laptops to access the network.
(Although I'm fully aware that a MAC can be forged ...)

---

