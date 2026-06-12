---
title: "[Sniff] MSN"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by herlock on 2006-12-27
Hello,

I would like to show to my friends that it would be great to use an IM wich is able to crypt the conversations. So I would like to show them that it's possible to sniff msn conversations.

I found two programs:
msniff and chatsniff but they couldn't sniff because i'm behind a switch.

Have you got an idea ?

Thank you and sorry for this very bad english.

---

### Post by funkenstein on 2006-12-27
tried ethereal?

---

### Post by dbott67 on 2006-12-27
Switches, unlike hubs, do not broadcast traffic through every port.  The switch maintains a table of the MAC address connected to each port and directs the traffic only to the destintation port.

In order to perform this type of activity on a switch, you need to poison the ARP cache.  This link doesn't explain how to do it, but it gives a good explanation of how it works:

[http://www.governmentsecurity.org/archive/t8123.html](http://www.governmentsecurity.org/archive/t8123.html)

NOTE: I'll leave your comment at face value that this is on your own network.  Keep in mind that more sophisticated networks monitor for this type of activity and the likelihood of getting caught is very high (you must provide your real MAC address to forward the traffic to, so you're providing your computer's DNA, so to speak).

---

