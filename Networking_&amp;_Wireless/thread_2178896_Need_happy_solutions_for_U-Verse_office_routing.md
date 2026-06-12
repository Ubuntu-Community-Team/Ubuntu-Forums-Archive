---
title: "Need happy solutions for U-Verse office routing"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by 1clue on 2013-10-05
Hi.

I have a Motorola NVG510 in my office.  This is a commercial account, we get 4 public IP addresses.  The ONLY ISP who will deliver to this building is AT&T and it's gotta be U-Verse.

Our public IP addresses are exhausted.  We need a solution.

You can google "NVG510 bridge mode" and you'll get an endless stream of misery.  Motorola makes exactly two routers which do not support bridge mode, and they were made that way expressly by request of AT&T.  I don't know why.  AT&T offers two routers, and guess what?  It's those two routers.

I'm not going to go into the details of the problem, it's all over Google.  So are unhappy solutions to the problem.

So what I want from you guys is this:  Has anyone taken a Linux box and set it up as a router behind a U-Verse connection?  Here's my proposal:
[LIST=1]
[*]Two NICs
[*]Grab one of the public IPs with the external NIC.
[*]Route ports and protocols to the internal NIC per a map, giving the internal network a clean environment?
[/LIST]

This seems to be a no-brainer, but we're dealing with a company who has gone out of their way to disable their junky router.  I want to hear from somebody who's done it.

Thanks.

---

