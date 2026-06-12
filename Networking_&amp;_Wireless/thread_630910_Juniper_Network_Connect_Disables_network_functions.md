---
title: "Juniper Network Connect Disables network functions on disconnect - UB 7.10"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by sebutler2 on 2007-12-03
I'm currently using UB 7.10... 

I have have a Juniper network connect that I have setup using instructions on this forum.. Since I have upgraded to 7.10, when I disconnect from the juniper network connect it kills my lan connection and I can no longer access my local network..To resolve the issue I must restart the machine.  Has anyone seen this before?

---

### Post by caseyboardman on 2008-01-03
I have seen this.  In fact, I am on my laptop now so I can try to find a solution and test it.

So far I know that I can't get to the internet, but I can get to my router.  I'll post back if I find anything.

---

### Post by caseyboardman on 2008-01-03
I went into my Network Settings, unchecked my wireless connection (that's the connection I'm using), and closed it.  I verified that I couldn't connect to anything (no router, no nothing).  I then went back into the Network Settings, checked the wireless, and closed it.  Voila!  

Not ideal, for sure, but better than a reboot.  I did have to do some workarounds to get juniper working (there's a post in these forums somewhere that I followed), I'm not sure if this issue is an artifact of that or a separate problem.

---

### Post by sebutler2 on 2008-01-03
Thanks for the feedback... I agree. When I disable and re-enable the network interface it does re-establish network connectivity.

---

