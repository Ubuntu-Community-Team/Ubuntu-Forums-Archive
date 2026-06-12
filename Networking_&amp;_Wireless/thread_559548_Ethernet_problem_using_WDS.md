---
title: "Ethernet problem using WDS"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by mcmwing on 2007-09-25
I recently moved a computer running Ubuntu 7.04 to a new location.  Because this computer does not have a wireless card and is not in a location that can be easily wired, I had to connect it to a wireless router that was associated using WDS to the main router.

The problem is, using Ubuntu, the computer cannot connect to the outside Internet.  It can only access the local network, and other computers can connect to it fine.  When I go to the main router's configuration page, I am instead presented with the WDS router's config page.  The only way I can get online is if I connect yet another router to the WDS router and connect the computer to that router.

This behavior does not happen with Windows (it connects fine using only the WDS router).

I have checked the routing tables in Ubuntu, but do not see anything off; it shows that it has an IP assigned from the correct router, and the gateway appears to be correct.

Any ideas on how to fix this?  Or am I stuck using multiple routers?  This daisy chaining isn't exactly the solution I want.

---

