---
title: "Wake-On-Lan Router Reboot Problem"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Matuku on 2009-09-18
So I've finished setting up wake-on-lan for my home server and it works great; from any outside PC or local PC I can just wake up the server and ssh in.

But when I reboot the router then it just stops working. Even from local PCs it tells me it's sending the magic packet when I command it to do so but then nothing happens; no server starting up. The only thing I can think of is that the router is "forgetting" which static IP address applies to the server's MAC address (or the other way round) as the server is off and hence doesn't currently have an IP address; therefore the router can't decide where to forward the magic packet on to. Does this seem likely and can anyone suggest any solution?

---

