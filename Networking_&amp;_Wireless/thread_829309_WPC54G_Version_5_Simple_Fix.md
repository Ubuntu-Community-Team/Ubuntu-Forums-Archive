---
title: "WPC54G Version 5 Simple Fix"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by mr_boo1711 on 2008-06-14
Hey folks!

Just in case anyones having problems with this version of the Linksys card (I've not seen ANY other posts regarding the version 5 so far).

Its easy sorted by installing and using ndiswrapper - just point ndis at the file named 'lsmvnds.inf' (Which is part of the Win XP driver package) NOT the file 'lsbcmnds.inf' which has been mentioned in posts about other card versions.  Worked the second I clicked the button. :D

Incidently - The version 5 drivers are NOT available through the Linksys website and are a nuisance to find, so if anyone needs these just PM me and I can e-mail them over.

Job jobbed. ;)

Steve

---

### Post by kevdog on 2008-06-14
Have you pm'd Jamie Jackson about this find?  I think he would find this extremely useful since he maintains a very good ndiswrapper/driver repository.  If you need help finding him, let me know, but please report this to him!

---

### Post by mr_boo1711 on 2008-06-15
> **kevdog said:**
> Have you pm'd Jamie Jackson about this find?  I think he would find this extremely useful since he maintains a very good ndiswrapper/driver repository.  If you need help finding him, let me know, but please report this to him!

Done! :D

---

### Post by Jamie Jackson on 2008-07-03
> **mr_boo1711 said:**
> Done! :D

Turns out it's not a Broadcom, but thanks.

---

