---
title: "I can not see my pointer?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by WolfRage on 2009-10-30
I can not see my mouse pointer after a restart. I can only locate it by hitting ctrl and then it gets highlighted for a few seconds. System is Ubuntu Studio 9.10 With Compiz disabled. WTF?

---

### Post by WolfRage on 2009-10-30
I fixed the problem instantly by adding this:
[B]Option       "Backingstore"      "true"
Option       "HWCursor"          "off" [/B]
To my **etc/x11/xorg.conf**    configuration file.  It appears the culprit was a video game that had not shutdown properly.

---

