---
title: "Router allows second IP address"
date: 2023-04-22
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2023-04-22
I've got a TP-Link Model No. TD-W9970 router, not the most elaborate of  devices I know but there is an option to set a second IP address.  Not  to be confused with a virtual LAN, this option is available, creates a  different subnet with its own DHCP range.

I may be missing something obvious but am wondering why would one need a  second IP address for a router.  Just to see the effect I created a  second IP address within a different subnet, works fine, can access  router configuration via second address but wee bit baffled as to  purpose.

Anyone any ideas?

Geffers

---

### Post by TheFu on 2023-04-22
WAN side?  There are lots of reasons.  Perhaps you have redundant ISPs - say you have both fibre and cable ISPs and having any downtime at home would cost you money - much more than a $150/month ISP bill.

On the LAN side, there are lots of reasons to have different subnets and for enterprise class routers, running in a redundant setup, a floating IP or 2 can be shared between routers for HA and load balancing.

That's a really old router you have.  Probably lost support at least 5 yrs ago. There are lots of security problems, especially if you use the wifi at all in any router that hasn't been patched in the last 2 yrs.  Not to mention there are always security issues with routers that need to be patched every quarter.  As a rule of thumb, if a router hasn't gotten any new firmware in the last 90 days, it is time to replace it.

With the new router, you might want to consider a different brand that has a history of long support periods and following best practices for router security.

---

### Post by Geoff_Lane on 2023-04-25
Been thinking for some time to use a R-Pi running open-WRT and a GBit switch, used to have a Draytek pre fibre days, that was a decent device.

Geffers

---

### Post by TheFu on 2023-04-25
> **Geoff_Lane said:**
> Been thinking for some time to use a R-Pi running open-WRT and a GBit switch 

Not a good idea for many reasons.

---

### Post by Geoff_Lane on 2023-04-30
> **TheFu said:**
> Not a good idea for many reasons.

Appreciate from previous posts that your knowledge of Linux is far greater than mine but I have read that an excellent option is a router (such as many linksys versions) that can take a firmware installation of open-Wrt.

I have experimented with it (on a Pi) briefly and it certainly appears considerably more configurable than most stock routers.

Geoff

---

### Post by TheFu on 2023-04-30
It isn't about the OS or router setup.  It is about the terrible hardware.  Get better hardware.  There are some failures in raspberry pi hardware that have security implications.  That's what happens with the cheapest stuff.  BTW, the cost of a faster R-pi v4 is beyond what a low powered x86-64 system would cost which was specifically designed to be a router with multiple, quality, intel NICs.  I've got almost 10 yrs on an APU2 system.  All in, it was $144 and runs almost any router distro. I use opnsense, but open-WRT is fine.  I expect the APU2 to meet my needs for another 2 yrs.

---

