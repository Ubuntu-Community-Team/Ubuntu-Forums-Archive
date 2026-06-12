---
title: "Is there a way to undo any changes in last hour (Synaptic, and &quot;Add/Remove)?"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2010-07-06
My version of mplayed seems screwed up after deleting it and restoring it, some stuff must have returned differently. So, is there a way to go back in time i guess to reverse changes made?

---

### Post by Yarui on 2010-07-06
Do you mean like a system restore in Windows?  I don't think anything like that comes bundled with Ubuntu.  What do you mean when you say it seems screwed up?  Have you tried running:
```
sudo apt-get remove --purge packagename
```
Replacing packagename with the name of the installed package.  Then reinstalling the package.  using --purge will do a more complete removal so reinstalling the application after this may give you different results.  If that doesn't fix it you may have to manually fix the problem.

---

### Post by pdlethbridge on 2010-07-06
In synaptic, under file / history you can find a list of programs that you added or deleted. It won't make any changes automatically, but it will show you what you have done in the past days or weeks.

---

### Post by DesiArnez6 on 2010-07-07
Thx, I did end up finding the Synaptic "History" and with that I was able to undo the damage. :)

---

### Post by pdlethbridge on 2010-07-07
that's great, please mark the thread solved

---

### Post by kusharan on 2011-05-21
is the same feature available when you install packages through sudo apt-get install via the terminal. I mean like through a log file.

---

### Post by cb5online on 2011-12-03
Thanks, that info just helped me out :)

---

### Post by cmcanulty on 2011-12-03
ubuntu tweak also has 3 backup-restore functions

---

