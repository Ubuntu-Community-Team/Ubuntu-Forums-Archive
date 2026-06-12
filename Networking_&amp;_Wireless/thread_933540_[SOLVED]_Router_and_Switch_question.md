---
title: "[SOLVED] Router and Switch question"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by aimpau on 2008-09-29
I'm planning to connect my PC and wired canopy to a switch through LAN connection. My question is that would the switch automatically assign an IP to both my PC and canopy?

Or do I need a router for this kind of situation?

I'm trying to access my canopy since it has DHCP enabled, thus can't access it the usual way.

---

### Post by Iowan on 2008-09-29
*Ordinarily*, a switch won't have DHCP server built in - so it won't/can't assign IP's.

---

### Post by jmbargar on 2008-09-29
You need to get at least two differents ip addresses. One of them will be for your PC and the other one will be for the canopy. A switch is not a good option in order to assign automatically ip addresses to differents devices because it hasn't a dhcp server inside, so a switch needs a router behind.

---

