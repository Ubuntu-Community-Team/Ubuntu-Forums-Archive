---
title: "Very Confused Wireless"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by viergeame on 2007-09-02
My Network Manager icon says I have no connection, but I do.  It's a bit slow, but my connection speed seems to vary a lot anyways.  This is a fresh Feisty install.  I have been running Feisty on my other hard drive and never seen this issue.  Has anyone else seen this, or is my computer going insane?

---

### Post by plewisfdx on 2007-09-03
I just started looking into network manager last night when I had problems.  Network manager only manages devices that are *NOT* configured in /etc/network/interfaces.  So if you have the device configured correctly "manually" in this file (or by "system->administration->network" ... same thing) it will connect with network manager not knowing anything about it.

If it works fine for you this way, I would leave network manager out of the loop.  I accidentally joined my network with network manager yesterday and am not able to switch back successfully to manual after doing it manually for years.  And now I have to type in my network key every boot up.

---

### Post by viergeame on 2007-09-03
I didn't plan on messing with it again unless it stopped working.  But if it was a problem I wanted to be prepared to fix it.

What I still find really weird though, is that with the exact same setup on my other install network manager deals with it.  

I guess I will just leave it alone unless it breaks.  No need to argue with something that works.

---

