---
title: "Stripped-down gnome?"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-12-23
I'd like to install a barebones version of the Gnome desktop on top of Ubuntu Server. In other words, I'd like to get the panel, menu, fonts, etc. that come with "ubuntu-desktop," but I don't want all of the applications (OOo, rhythmbox, ekiga, etc). Is there some way to install just the desktop environment without all of the bloat?

Thank you!

---

### Post by bwang on 2008-12-23
Try this:
```

sudo apt-get install xorg gnome-core gdm

```

---

### Post by doctorbighands on 2008-12-23
Thank you!

I've read that there are issues with insufficient fonts when installing gnome-core. Is that true? If so, how is that fixed?

---

