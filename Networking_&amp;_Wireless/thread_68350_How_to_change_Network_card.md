---
title: "How to change Network card?"
date: 2005-09-22
forum: Networking &amp; Wireless
---

### Post by GOwin on 2005-09-22
Hi. I'm having a problem with an ethernet card that would just "die". In the syslog, I would see logs " kernel: NETDEV WATCHDOG: eth0: transmit timed out".

I've tried passing "noapic" to the kernel but it did not resolve the problem. So I'm planning to change the LAN card instead.

Would this be a plug and play thing? If not, what should I do after I change the card?

Thanks.

---

### Post by cwaldbieser on 2005-09-23
[QUOTE=GOwin]Hi. I'm having a problem with an ethernet card that would just "die". In the syslog, I would see logs " kernel: NETDEV WATCHDOG: eth0: transmit timed out".

I've tried passing "noapic" to the kernel but it did not resolve the problem. So I'm planning to change the LAN card instead.

Would this be a plug and play thing? If not, what should I do after I change the card?

Thanks.[/QUOTE]
Like most modern computer systems, the answer is a qualified maybe.

It should just work, but sometimes it doesn't.  Your system recognizes a lot of different hardware, but there are definitely some cards that won't work or might require configuring.

You can try grepping through "lspci" and "dmesg" to make sure it was detected.  It may also be a good idea to visit the manufacturer's web site and see if they have any instructions about installing drivers, etc.  I have found that most manufacturers try to be helpful if you tell them what you are trying to do,

---

