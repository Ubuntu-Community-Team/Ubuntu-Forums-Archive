---
title: "Gnome-screensaver"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by tesseract1 on 2009-07-28
I can't seem to get my screensaver to work.  It fades to the screensaver after the allotted idle time and then immediately goes away.  This keeps happening after each idle interval.

The screensaver always begins to appear but then immediately stops.

Any ideas?

---

### Post by tesseract1 on 2009-07-29
Still an issue for me.  I can't seem to find any support.

---

### Post by llamabr on 2009-07-29
the gnome screensaver is pretty -- whatever is the opposite of configurable.

Try installing xscreensaver.  i don't know why a crappy program replaced a perfectly functional one.

---

### Post by tesseract1 on 2009-07-29
Yea I tried xscreensaver.  It works but the screensavers on it are blah.  Gnome has better ones, I want to fix it!

---

### Post by Volt9000 on 2009-07-29
Actually xscreensaver has a LOT of extra screensavers, if not many installed by default.

You can install the extra ones with the following terminal command:

```

sudo apt-get install xscreensaver-gl xscreensaver-gl-extra 

```

There's a nice article on how you can retain gnomescreensaver but have xscreensaver control it, and allow you to configure. It's a bit of a roundabout way, but works quite well.

[http://ubuntuforums.org/showthread.php?t=198809](http://ubuntuforums.org/showthread.php?t=198809)

---

