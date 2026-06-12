---
title: "[SOLVED] Segmentation Faults!!"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by appi2012 on 2008-12-27
I can't start rhythmbox, eog, totem, and many other programs. To check for the problem, I ran them from the terminal, and the output was simply
```
gtk
Segmentation fault

```

I thought maybe it was because I recently installed pygtk and pygobject from source, so I uninstalled those. After doing so, rhythmbox ran once from the terminal, but all further trials had no outcome. So now I'm stuck, and can't browse my media, view videos or images. Please help!

Thanks in advance.

---

### Post by appi2012 on 2008-12-27
any ideas?  please?

---

### Post by Cl0ud9 on 2008-12-27
I don't know why you are getting a segmentation fault, but I do know that segmentation faults are generally caused by illegal memory access.

Perhaps, something was installed and run that has a memory leak. In this case rebooting will fix your problems. It's worth a shot.

---

### Post by appi2012 on 2008-12-28
Thanks for the response - will do.

---

### Post by appi2012 on 2008-12-28
I figured it out. A quick google search led me to another ubuntu forums post (which the official forum search didn't find) which gave me all the answers. Firstly, it didn't start after I installed pygtk because after that, I tried to create a gtk window in python, and saved the file as gtk.py, and compiled it as gtk.pyc . Now, according to the other post, rhythmbox doesn't like my broken script, and crashes when it tries to load it. However, starting it in another directory which doesn't have the file works perfectly. This explained the one time it did start from the terminal, but that was only because my working directory was ~/pygobject-2.15 (or something like that) because I just uninstalled that program. So I deleted my useless scripts, and wala, Rhythmbox started!!
:lolflag:

Thanks anyway for your help.

---

