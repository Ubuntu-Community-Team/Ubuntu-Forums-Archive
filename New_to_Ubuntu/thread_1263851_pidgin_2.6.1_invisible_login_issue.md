---
title: "pidgin 2.6.1 invisible login issue"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by infestor on 2009-09-11
i am experiencing a problem with pidgin login. it is set to invisible, but each time i login i appear to be available. then i have to manually select invisible. pretty annoying. any solution to that guys?

---

### Post by mcduck on 2009-09-11
In Pidgin go to Tools/Preferences, and on the Status/Idle -tab mark the "Use status from last exit at startup"-checkbox (or set the startup status to whatever you want in the same place).

---

### Post by infestor on 2009-09-11
> **mcduck said:**
> In Pidgin go to Tools/Preferences, and on the Status/Idle -tab mark the "Use status from last exit at startup"-checkbox (or set the startup status to whatever you want in the same place).
  i am sorry but that doest solve the problem. pidgin insist on signing me in as available.

---

### Post by mcduck on 2009-09-11
> **infestor said:**
> i am sorry but that doest solve the problem. pidgin insist on signing me in as available.

In that case I can't help you. That's where the sign-in status is configured, and it definitely works fine for me.

---

### Post by r.osmanov on 2009-09-11
Maybe something is wrong in your config files. 
Try the following:

[LIST=1]
[*]Stop pidgin
[*]move ~/.purple to a different location
[*]Start pidgin
[/LIST]
Probably, it will create a new profile, and it will work as it should.

---

