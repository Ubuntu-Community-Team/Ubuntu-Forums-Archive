---
title: "Wired Ethernet not Enabled on Startup"
date: 2018-03-15
forum: Networking &amp; Wireless
---

### Post by Jason_Hunter on 2018-03-15
I don't understand why wired Ethernet is disabled when starting GNOME. 

I've found a few references as to how I can fix this, but I don't understand why it is like this in the first place?

I also recently upgraded to 17.10 and it didn't ask me any question about overwriting any config files, if that was the problem.

---

### Post by TheFu on 2018-03-15
Ethernet should connect before any login.  It should be part of the system, not any userid.
17.10 changed the way networking is configured. netplan is the new version to solve issues that a few people experienced.  Not using an LTS release isn't something I do.  6 months of support just isn't sufficient for my needs.

So, to begin we need to figure out what is broken.  Driver, cables, ports, or configuration?  I always start by trying to ping the router by IP address. If that doesn't work, we don't need to look outside the computer, usually.

BTW, your first sentence implies that if you use a different DE, then networking works?  Does it?

---

