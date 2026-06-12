---
title: "some applications wont start"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by libihero on 2009-11-21
wow im hitting the boards hard today
sorry for being annoying and thank you all for those who helped :)
anyways a couple of my applications don't even start.  one is gnome color chooser.  in the terminal i get this when i try to start it:

```
~$ gnome-color-chooser
Welcome to gnome-color-chooser version 0.2.5 for i486-pc-linux-gnu

Loading GUI with libglade.. done
Initializing and starting gnome-color-chooser.. Couldn't load gnomecc theme '/home/hamza/.gnome-color-chooser/config.xml'!
done

GLib-GObject-ERROR **: Attempt to add property GtkMenuBar::local to class after it was derived
aborting...
Aborted

```

---

### Post by libihero on 2009-11-22
bump... 
i really need gnome-color-chooser :( lol

---

### Post by NoaHall on 2009-11-22
Can you post the output of the other application which doesn't work?

---

### Post by sandyd on 2009-11-22
your bug is related to 
[https://bugs.launchpad.net/gnome2-globalmenu/+bug/474488](https://bugs.launchpad.net/gnome2-globalmenu/+bug/474488)
a lot of people are having this problem, which seems only to occur in karmic.....

FIX:
see last post of [http://ubuntuforums.org/showthread.php?t=1289649](http://ubuntuforums.org/showthread.php?t=1289649)

---

