---
title: "sharing internet w/ windows w/ hub"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by bobbybobington on 2007-01-15
ok, i decided to be a 5 port hub to share the internet with my windows pc and my ubuntu pc. The hub is connected to each comp, and to the cable modem. The problem is that i can only get only one comp connected to the internet at a time, and i'm a noob when it comes to networking. (I usually put in random ip addresses, and fart around with options untill i get an internet connection in ubie). So what do i have to do to get the two comps to share internet?:confused: :confused: :confused:

---

### Post by PilotJLR on 2007-01-15
Random IP addresses, as we say in the `biz, are a "Bad Thing."  :-)

You need a router, not a switch/hub. If one of the computers has a 2nd NIC, and you are so inclined, you could make a router...

Best advice would be to go to best buy or target or somewhere and get a cheap little $40 router.

---

### Post by bobbybobington on 2007-01-15
ok, after some digging, i think that i need a router that uses dhcp. The hub i have doesn't have this? So once i get the router, all i need to do is select dhcp in networking, and then im all set. Do i have this right?

---

### Post by PilotJLR on 2007-01-15
Exactly right.

Hubs provide you NOTHING other than amplification.

A soho router will have DHCP enabled by default... it provides NAT and DHCP, and you need both of those.

---

### Post by bobbybobington on 2007-01-15
well, that simplifies things. Thanks a lot for the clarification:D . Ill have to work on figuring out  ips though...:-k .

---

### Post by PilotJLR on 2007-01-15
No problem!
Basically, IP addresses can be public or private.. the dhcp service on the router will assign addresses like 192.168.1.x, which is private. The NAT function of the router then "translates" multiple private IPs into a single public IP (which is your internet connection). This is the mechanism that allows multiple machines to share 1 connection (one public IP).

---

