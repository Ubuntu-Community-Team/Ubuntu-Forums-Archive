---
title: "Network not working after power loss"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by bysse on 2008-10-17
Well, i lost power to my machine and when i started it again i couldn't get any IP. I tried plugging in the cable in my laptop and it worked fine. Then, after stopping the network, i tried with a live cd on the first machine without any success. 

Then i ran tcpdump, and it turns out that the interface receives arp-packets from the router but no ip-packets. Strange.

The NIC i'm using is integrated with my motherboard, p5n32-e sli (nForce 680i chipset), and i'm running 8.04 amd64.
I've updated my BIOS and also rebooted and restarted the network many times just to be sure.

The only thing i haven't tried yet is a CMOS reset but other than that i don't now what to try. 
Anyone got any idea?

Please?

---

### Post by superprash2003 on 2008-10-17
does it work with a static ip?

---

