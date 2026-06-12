---
title: "[SOLVED] Two versions of Sun Java??"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-12-24
Hi all, I've been browsing through Synaptic and I see that I've got two versions of the Sun Java Runtime Environment installed on my machine (ubuntu 8.10 Intrepid).

Both sun-java6-jre (6-10-0ubuntu2) and sun-java5-jre (1.5.0-16-3) are showing up as being installed.

Isn't java6 a more recent version of the jre? Why would I still have 5 installed? Could I safely uninstall 5?

Shouldn't both of these packages have the other listed as a conflict?

---

### Post by igknighted on 2008-12-24
> **Roger Allott said:**
> Hi all, I've been browsing through Synaptic and I see that I've got two versions of the Sun Java Runtime Environment installed on my machine (ubuntu 8.10 Intrepid).

Both sun-java6-jre (6-10-0ubuntu2) and sun-java5-jre (1.5.0-16-3) are showing up as being installed.

Isn't java6 a more recent version of the jre? Why would I still have 5 installed? Could I safely uninstall 5?

Shouldn't both of these packages have the other listed as a conflict?

both can coexist, and there could be conceivable reasons why you would need both (many java apps don't like changes made to the new JRE, similar to how ubuntu still ships with quite a few gcc versions).  You can use the update-alternatives command to pick which one is used as default.

EDIT: They are completely independent, so you could remove whichever one you dont want.

---

### Post by Roger Allott on 2008-12-24
> **igknighted said:**
> both can coexist, and there could be conceivable reasons why you would need both (many java apps don't like changes made to the new JRE, similar to how ubuntu still ships with quite a few gcc versions).  You can use the update-alternatives command to pick which one is used as default.

EDIT: They are completely independent, so you could remove whichever one you dont want.

Thanks. I just needed reassurance really that my system wasn't going to blow up! Oh well, 5 has now gone and everything still functions OK, so far.

---

