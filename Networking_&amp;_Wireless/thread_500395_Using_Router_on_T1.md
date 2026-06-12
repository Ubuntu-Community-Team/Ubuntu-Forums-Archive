---
title: "Using Router on T1"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by jmedina on 2007-07-13
Hello, I just purchased a regular router so I can turn the business I work at into a Hotspot. I'm pretty sure that the main connection for the building is T1. Will this work if I plug it in?

---

### Post by Mr. C. on 2007-07-13
A T1 CPE essentially converts the signal from the phone company to standard Ethernet TCP/IP. 

You can connect any Ethernet device on the LAN side of the T1.  You are responsible for managing the IP address(es) provided by your ISP.  If you have only one IP address, you will have to use some NATing device to provide additional IPs as required by your LAN.

MrC

---

### Post by mips on 2007-07-14
Who owns/rents the T1 coming into your building ? Chances are it is already terminated on a router.

You are very vague with information. Speak to your it people.

---

