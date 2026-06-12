---
title: "bcm43xx and new kernel"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by svenaron on 2006-07-24
Hi.

Im running Dapper on a Dell X300 with a Broadcom 4306 wireless miniPCI card.
Everything is happy joy-joy, I'm using network-manager and can connect to pretty much every wireless AP I've encountered.

Problem is that every time I upgrade my kernel I need to copy/hardlink/symlink the bcm43xx* files into /lib/firmware/<kernel_version>/  
I have been searching this forum for a more automatic solution but to no avail. Anybody know of a solution to this?
I suppose I could just solve it with a script or something but I would rather  have a more elegant solution.

best regards
/Sven

---

