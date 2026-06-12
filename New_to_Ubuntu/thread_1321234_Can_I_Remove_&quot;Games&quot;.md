---
title: "Can I Remove &quot;Games&quot; ?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by darksideforge on 2009-11-09
I know that if I want to remove a program like ekiga that I never use, I would:
```
sudo apt-get remove ekiga
``` .
However, is it possible for me to remove all of the games (which I never use) with something similar to:
```
sudo apt-get remove games
``` ?

Sorry for the silly question. I've often thought about it but never tried it.

If all else fails I suppose I could just start with a Minimal install like this one [http://ubuntuforums.org/showthread.php?t=1155961.]("http://ubuntuforums.org/showthread.php?t=1155961.")

---

### Post by coldReactive on 2009-11-09
As of 9.10, the gnome-games metapackage does not remove any of the games. You have to remove them all manually from add/remove, synaptic or the software center.

I'm assuming you're using Ubuntu, as the gnome metapackage won't install due to broken dependencies in 9.10.

---

### Post by ranch hand on 2009-11-09
Just go to synaptic and click on search.  Type "games" and hit enter.  All the installed oneswill have colored in boxes.  Mark for removal.  Hit "apply".

When it is done click on "status" (bottom left of page) and see if there is any residual stuff listed and not installed put having left overs.  Mark all of them for "complete removal".  Hit "Apply".

Synaptic is the best gui that you will find.  It is the place to go to find what is installed.  Explore it.  I think you will find it worth your while.

---

### Post by darksideforge on 2009-11-10
I started using Ubuntu with 8.04, then upgraded to 8.10; Fresh installed 9.04, tried 9.10b4 and hated it so went back to 9.04.

I've been running 4 different servers, both headless and with GUI, but I guess what's different is that every time before I was trying "Completely Uninstall" and that was breaking my gnome-desktop.

By uninstalling individually, it worked like a charm...thanks guys!

---

