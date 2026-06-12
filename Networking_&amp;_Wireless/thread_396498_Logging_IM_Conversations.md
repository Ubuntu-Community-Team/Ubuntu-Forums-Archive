---
title: "Logging IM Conversations"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by earlpotter on 2007-03-29
Hello All, 

I've been researching this on and off on the net for a bit and can't seem to find the solution.


I would like to be able to capture/log IM conversations in and out of a network.  

Would I use squid for something like this?

My firewall is m0n0wall 1.23, so transparent proxy is not possible.  But I could allow all web access thru the proxy.

Any suggestions or resuorces or howto's would be appreciated.

Thank you.

---

### Post by Mr. C. on 2007-03-29
Squid is a web cache, not a general TCP filter.

Some chat channels will be encrypted, and you will be able to decypher them.

Clear text channels are available to any sniffer.

MrC

---

