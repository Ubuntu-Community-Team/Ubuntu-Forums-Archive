---
title: "Cannot connect to a hidden ssid"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by bbmak on 2007-06-19
I am using Ubuntu 7.04
Wireless card PCMICA, Asante AL5410G

When i broadcast my ssid, i am able to connect to the router, but when I am not broadcasting the ssid, the card cannot connect to the router.

Are there any option that will allow the card to connect to hidden ssid ????

---

### Post by Mr. C. on 2007-06-19
I've seen this with serveral AP / card combinations.  I suspect there is a bug in the card driver, but have never chased it further down the debugging path.  I've been able to workaround it in all cases simply be enabling broadcast, connecting once, and then disabling.

Sorry, no better answer,
MrC

---

### Post by bbmak on 2007-06-19
Can you use a windows driver (Ndiswrapper) to solve this problem? because the card is okay in Windows.

---

### Post by Mr. C. on 2007-06-19
This further agrees with my assumption about where the problem resides.

Sure, give it a try.
MrC

---

