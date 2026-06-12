---
title: "where did all the screensavers go?"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by libihero on 2009-11-04
i remember ubuntu had tons of screensavers by default.  now with a fresh install of karmic, it looks like there are barely any.  how do i get the rest back?

---

### Post by The Funkbomb on 2009-11-04
I'm pretty sure you can install some through synaptic.

---

### Post by undecim on 2009-11-04
try installing xscreensaver-data and optionally xscreensaver-data-extra packages. They contain the screensavers that come with xscreensaver, but should also show up in gnome's screensaver

---

### Post by jason.b.c on 2009-11-04
> **undecim said:**
> try installing xscreensaver-data and optionally xscreensaver-data-extra packages. They contain the screensavers that come with xscreensaver, but should also show up in gnome's screensaver

That will wind up installing "xscreensaver"

then you end up with two differant entries in your menu..

---

### Post by libihero on 2009-11-04
how do i make it so its all in "screensaver"?

---

### Post by undecim on 2009-11-04
> **jason.b.c said:**
> That will wind up installing "xscreensaver"

then you end up with two differant entries in your menu..
No, xscreensaver is not a dependency of xscreensaver-data. the command "sudo aptitude install xscreensaver-data" installs only the xscreensaver-data package

---

