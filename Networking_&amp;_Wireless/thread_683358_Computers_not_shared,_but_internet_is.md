---
title: "Computers not shared, but internet is?"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by ed-koala on 2008-01-30
I'm having trouble figuring this out, and the posts seem to all lead me in circles.
I'm running Gutsy on my main PC, and Vista on another PC.  I have a Linksys router, and a Westell DSL modem.  I got internet connection sharing set up so both machines are communicating with the router/modem, but I cannot seem to get each PC to see the other on the network.  I'd appreciate a step by step guide to set up Gutsy then Vista so I'll be able to share files between both machines.  I also want to share my printer which is connected to the Ubuntu machine so I can print from Vista (even tho there are no drivers for this Lexmark for Linux).

Let me know what output is needed so someone can figure this out.  I installed Samba, and I see a Windows Network, but no PC is listed under MSHOME  workgroup.

---

### Post by chewearn on 2008-01-31
Can the boxes ping each other in the network?

---

### Post by ed-koala on 2008-02-01
Nope, it's like they are not there at all, and my network is just one PC.   I'm suspecting it might have something to do with my modem not being set up correctly.  I didn't change it before hooking up the router and both are probably acting as router ... I plan to check that later today and see what happens.   I'll probably start from scratch ... but, is it a good idea to uninstall anything like Samba before starting over?

---

### Post by ed-koala on 2008-02-02
bump

---

### Post by Twizzle on 2008-02-02
Have you played around with the firewalls?

Try disconnecting your router / modem from the internet but leaving both the computers connected. Then turn off all firewalls and try to connect.

---

### Post by mips on 2008-02-02
> **Twizzle said:**
> Have you played around with the firewalls?


Firestarted blocks ICMP but you can unclick it in the setup somewhere.

---

