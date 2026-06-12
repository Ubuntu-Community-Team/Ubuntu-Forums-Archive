---
title: "Is it possible to put the main toolbar and location bar NEXT to each other (Nautilus)"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by the8thstar on 2010-01-01
Hello,

I've been trying to find ways to put the main toolbar and the location bar net to each other in Nautilus but they always end on top of each other. Is there a way to accomplish this (gconf-editor or else)?

Thanks in advance for your help. And a happy new year to you!

---

### Post by Paqman on 2010-01-01
Edit: Ah sorry, didn't see that meant in Nautilus...

---

### Post by the8thstar on 2010-01-01
I am not talking about panels.

Here is what I mean in the attached screenshot. I want both bars to be on the same level, next to each other. In the screenshot they are on top of each other.

---

### Post by mechro on 2010-01-01
I can't find anything in gconf that will do it.

There may be an .xml file you could tweak in /usr/share/nautilus/ui but I couldn't tell you which one might work.

---

### Post by the8thstar on 2010-01-01
> **mechro said:**
> I can't find anything in gconf that will do it.

There may be an .xml file you could tweak in /usr/share/nautilus/ui but I couldn't tell you which one might work.

Thanks for the idea. I checked each file, but it doesn't seem like this sort of option is available there.

---

### Post by the8thstar on 2010-01-01
I found this, which is pretty much what I had in mind. Just in case anyone is following this thread.

[http://davidsiegel.org/nautilus-simplified/]("http://davidsiegel.org/nautilus-simplified/")

---

### Post by the8thstar on 2010-01-02
BUMP - is a patched Nautilus the only way to go?

---

### Post by mechro on 2010-01-02
> **the8thstar said:**
> BUMP - is a patched Nautilus the only way to go?

I would say so. You could try different file managers.

KDE's **Konqueror** is highly configurable and you can run it from a Gnome desktop.

I use **PCMan** for browsing Folders with lots of images as Nautilus seems to seize up when it has to deal with large numbers of thumbnails. PCMan is not so configurable but it's already set up with the toolbars as you require.

---

### Post by the8thstar on 2010-01-03
Thanks I'll try PCMan and check if it can coexist with Nautilus.

---

### Post by mechro on 2010-01-03
By the way, Nautilus does have a "spatial" configuration. It gives you a minimal interface but it's probably too minimal...

In Nautilus Go to **Edit > Preferences >  Behaviour** - Uncheck "**Always open in browser windows**" Restart Nautilus.

---

### Post by mechro on 2010-01-18
@ the8thstar

Have you seen this?...

[http://ubuntuforums.org/showthread.php?t=1384617](http://ubuntuforums.org/showthread.php?t=1384617)

---

### Post by the8thstar on 2010-01-21
Yes I have! Thanks for the link, although I used the PPA repos in Ubuntu Tweak to get to the same result. 

I am extremely satisfied with the result.

---

