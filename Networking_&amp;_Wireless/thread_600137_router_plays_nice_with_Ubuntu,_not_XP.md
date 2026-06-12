---
title: "router plays nice with Ubuntu, not XP"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by DouglasAWh on 2007-11-01
Normally I would be thrilled that something worked in Ubuntu and not XP, but in this case, I've had lightning damage and really just want to get this back in order.  3 out of 4 of the connections on my router appear to be busted.  Wireless works just fine.  The 4th wired connection works in Ubuntu and not Windows.  I've tried three different Ethernet cards on this particular Windoze box.  I also tried a laptop a while back (though I can't remember for certain that I tried it on that 4th, just perhaps the others...which are def dead).

Is there any good reason for this to be the case?  Perhaps my Ethernet in my Dell laptop just r0x?  Here's the real kicker....it's a Microsoft router!  (don't hate me, it was a gift).  

Eventually, I'll read the documentation on connection sharing (and wait on my brother to give me his two wireless antennae's that are not in use), but I thought this issue of the router playing nice with Linux "out of the box" and not Windows was humorous.  Oh, one other note, I know for a fact one of the network cards I tried in Windows works, because when I hook it out to the laptop, the lights start blinking.  So weird.

---

### Post by SpiritIsReality on 2007-11-02
howdy
maybe after the strike, or with a new card you have to run the netwok wizard again?
[http://windowshelp.microsoft.com/Windows/en-US/help/baab4f1a-2461-482d-bb2e-c996a197e35f1033.mspx](http://windowshelp.microsoft.com/Windows/en-US/help/baab4f1a-2461-482d-bb2e-c996a197e35f1033.mspx)

[http://www.microsoft.com/windows/products/windowsxp/default.mspx](http://www.microsoft.com/windows/products/windowsxp/default.mspx)
[http://windowshelp.microsoft.com/Windows/en-US/default.mspx](http://windowshelp.microsoft.com/Windows/en-US/default.mspx)
[http://windowshelp.microsoft.com/Windows/en-US/Help/33307acf-0698-41ba-b014-ea0a2eb8d0a81033.mspx](http://windowshelp.microsoft.com/Windows/en-US/Help/33307acf-0698-41ba-b014-ea0a2eb8d0a81033.mspx)
trails

---

### Post by teknorah on 2007-11-03
> **DouglasAWh said:**
> Normally I would be thrilled that something worked in Ubuntu and not XP, but in this case, I've had lightning damage and really just want to get this back in order.  3 out of 4 of the connections on my router appear to be busted.  Wireless works just fine.  The 4th wired connection works in Ubuntu and not Windows.  I've tried three different Ethernet cards on this particular Windoze box.  I also tried a laptop a while back (though I can't remember for certain that I tried it on that 4th, just perhaps the others...which are def dead).

Is there any good reason for this to be the case?  Perhaps my Ethernet in my Dell laptop just r0x?  Here's the real kicker....it's a Microsoft router!  (don't hate me, it was a gift).  

Eventually, I'll read the documentation on connection sharing (and wait on my brother to give me his two wireless antennae's that are not in use), but I thought this issue of the router playing nice with Linux "out of the box" and not Windows was humorous.  Oh, one other note, I know for a fact one of the network cards I tried in Windows works, because when I hook it out to the laptop, the lights start blinking.  So weird.
What is the model of the Windows router?  Have you tried the support pages on Microsoft.com?  Have you logged into the router to check to see if there are any errors logged in there?  Have you tried different ethernet cables? Maybe 2 or 3 of them are bad and are causing confusion?  Are the ethernet cards installed, enabled and configured to use dhcp on your windows boxes? Is this router new (purchased after lightning storm)?  When did the issue start happening?

Without a bit more info (model of router, etc.), I am not sure anyone would be of much more help :)

---

### Post by Warren Watts on 2007-11-03
Another thought: Are the TCP/IP settings set correctly for your NIC ?

---

### Post by DouglasAWh on 2007-11-03
Figured out there must be some hardware differences.  I know everything is supposed to be industry standards but small differences in electrical output must be the problem.  Everything on the Windows side is fine.  The cable works with the Linux box and the Ethernet cards on the Windows box work fine when connected to the Linux box.  It may be that a different cable, with perhaps slightly different inconsistencies in wiring could work, but basically I think it was more-or-less just chance that anything worked on my friend router.  Until I can afford a new router, I guess I'll just be using all wireless.  Thankfully my brother had a couple wireless adapters he wasn't using.

---

