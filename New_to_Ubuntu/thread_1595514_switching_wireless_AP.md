---
title: "switching wireless AP"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by beew on 2010-10-13
Suppose you can access several wireless AP. Is there a way to configure Ubuntu so that it will automatically switch among them so that if one is getting too weak Ubuntu would connect to another one with stronger signals?

---

### Post by okplayer02 on 2010-10-16
no there is no such thing like that in Linux. theres no such thing like that in Windows. You must connect to a different wireless network manually.

---

### Post by marshmallow1304 on 2010-10-16
This is probably possible with a script or a custom program, but I don't think such a thing exists yet.
```
sudo iwlist <interface> scanning
```
provides information (including signal quality and level) about available APs.


If you scour the man pages for the various iw* utilities, you might be able to hack together a script.

---

