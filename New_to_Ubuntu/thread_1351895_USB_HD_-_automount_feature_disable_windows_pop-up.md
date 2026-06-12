---
title: "USB HD - automount feature: disable windows pop-up"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by nomnex on 2009-12-11
USB stick & USB external drive with several partitions.

Anytime I plug them in, nautilus pops-up a windows on the desktop for every volumes.

I am glad with the automount feature, but I want to get rid of the pop-up windows. How?

---

### Post by mustang on 2011-01-22
For future reference, I thought I'd post the solution to this even though it has been resolved by the author.

To disable the popup window when your USB HD gets auto-mounted, do the following:

Launch g-conf:
```

gconf-editor

```

Go to apps->nautilus->prefernces

And make sure **media_automount_open** is unchecked.

---

