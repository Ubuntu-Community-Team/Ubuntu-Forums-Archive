---
title: "My Ubuntu PC is just disappearing"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by randomjohn on 2007-12-03
I've got one PC (PCU) running Gutsy.  Another (PCV) is running Vista.  Another (PCX) is running XP.  They're all behind a Linksys WRT54GL (with dd-wrt, in case it matters).  PCU had been running stably for a while.  I didn't change anything on PCV or PCX.  PCU is headless and just has a bunch of drives and runs utorrent through wine (which I control through the fancy web ui most of the time).

I boot up in any order and PCV and PCX see each other and PCU just fine.  I have the PCU drives mapped on PCV.  It's all hunky dory for a while.  Then, for no reason I can figure out, I'll get an error from the utorrent webui that the request to PCU has timed out.  Or I'll be in PCV file manager and it will tell me that there's an error and "the local device name is already in use."  

Even if I try to get in by vnc by name or by IP, PCU is inaccessible.  I have to do a hard reboot because I can't even send a shutdown -r command or anything.  
That's ok right now while it's next to me, but it's supposed to be downstairs, since all it needs is power and network cable.

Any suggestions on troubleshooting?

---

