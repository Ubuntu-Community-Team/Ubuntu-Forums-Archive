---
title: "Help! Error w/Update, add/remove and synaptic"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by phreakphish on 2010-01-04
Hey,

I'm a fairly new user and I'm getting an Error when I try to use Update Manager, add/remove and Synaptic.

Error reads:

'E:Type '\u00e2\u0080\u0098deb' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

This happened when I tried to install a simple third party application "Blueman", a bluetooth manager.

Error also occurs in terminal.

Any help would be good. Thanks. Ubuntu 9.04; Sony Vaio Notebook.

---

### Post by philinux on 2010-01-04
```
gksu gedit /etc/apt/sources.list
```

Turn on line numbering from edit prefs and look at line 56.

It needs commenting out or deleting.

---

### Post by phreakphish on 2010-01-04
Thanks a lot, worked great.

---

