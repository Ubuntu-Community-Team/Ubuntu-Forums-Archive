---
title: "Question."
date: 2011-01-25
forum: New to Ubuntu
---

### Post by robgraves on 2011-01-25
Okay, first of all i'm pretty new to ubuntu and linux in general.  I just set up a dual boot system with windows 7 and ubuntu 10.10 just about a week ago, everything functions fine, but i decided to try out some of the other desktop enviornments, i believe GNOME is the default, so i downloaded KDE and Xfce also and i can switch between them, but it changed the appearance of my login screen and i prefer the old one better.  how do i switch it back?

---

### Post by fabricator4 on 2011-01-25
> **robgraves said:**
> Okay, first of all i'm pretty new to ubuntu and linux in general.  I just set up a dual boot system with windows 7 and ubuntu 10.10 just about a week ago, everything functions fine, but i decided to try out some of the other desktop enviornments, i believe GNOME is the default, so i downloaded KDE and Xfce also and i can switch between them, but it changed the appearance of my login screen and i prefer the old one better.  how do i switch it back?

I think it's changed the login screen so you can select the X environment to log into.

Go:

```

->system
    ->Admin
        ->Login Screen

```

and change it back to Gnome.  You might also need to change the GTK theme, where [this tutorial]("http://ubuntuforums.org/showthread.php?t=1445724") may (or may not) prove useful.

Chris

---

### Post by robgraves on 2011-01-26
from system >admin> login screen i do have it set to the gnome but i'mtrying to change the appearance of the login screen itself, i was looking through the link but i've noticed that under /usr/share/images i dont have an xsplash directory like many tutorials i've read seem to assume...

---

### Post by Smart Viking on 2011-01-26
You could reinstall gdm, doesn't take too long.

Btw, lrn2title, of course you have a question, that's why you made the thread. :P

---

### Post by Habeouscorpus on 2011-01-26
> **fabricator4 said:**
> I think it's changed the login screen so you can select the X environment to log into.

Go:

```

->system
    ->Admin
        ->Login Screen

```

and change it back to Gnome.  You might also need to change the GTK theme, where [this tutorial]("http://ubuntuforums.org/showthread.php?t=1445724") may (or may not) prove useful.

Chris

Meeehhhh.... I did this too, and ended up breaking stuff trying to get rid of it. Why didn't I find this earlier?

---

### Post by robgraves on 2011-01-26
lol, how do i reinstall the gdm?

---

### Post by Smart Viking on 2011-01-26
> **robgraves said:**
> lol, how do i reinstall the gdm?
This should do it.
```
sudo apt-get purge gdm && sudo apt-get install gdm
```

---

### Post by robgraves on 2011-01-26
> **Smart Viking said:**
> This should do it.
```
sudo apt-get purge gdm && sudo apt-get install gdm
```
AWESOME! that worked, thank you.

---

### Post by XBMC old School on 2011-01-26
> **robgraves said:**
> Okay, first of all i'm pretty new to ubuntu and linux in general.  I just set up a dual boot system with windows 7 and ubuntu 10.10 just about a week ago, everything functions fine, but i decided to try out some of the other desktop enviornments, i believe GNOME is the default, so i downloaded KDE and Xfce also and i can switch between them, but it changed the appearance of my login screen and i prefer the old one better.  how do i switch it back?


Please specify subject in the Title: portion. Question is very general.

---

