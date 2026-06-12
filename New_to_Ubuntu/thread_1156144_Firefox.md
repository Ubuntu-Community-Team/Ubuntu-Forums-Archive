---
title: "Firefox"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by elleppahc on 2009-05-11
Can some one help me.
My minimise, maximise and off buttons have vanished from the tool bar.
How can I restore them?
Have tried reinstall to no avail

---

### Post by Didius Falco on 2009-05-11
> **elleppahc said:**
> Can some one help me.
My minimise, maximise and off buttons have vanished from the tool bar.
How can I restore them?
Have tried reinstall to no avail

A couple of questions:

Is it just Firefox doing this, or all programs?

Are you using Compiz?

Are just the buttons missing or that whole top part of the menu bar?

---

### Post by Alterax on 2009-05-11
My experience with this ties back to compiz, aka "Desktop Effects".  Try turning them off within system > preferences > appearance and see if that takes care of the problem.

If it does, then I'd look into why Compiz isn't working out for you.

---

### Post by philinux on 2009-05-11
system>prefs>compizconfig settings manager

If not installed install from synaptic.

Click the extras option on the left.

Untick then tick the Windows Decoration box.

---

### Post by lovinglinux on 2009-05-11
Have you tried hitting F11?

These issue is occurring a lot lately. Firefox is starting in full screen mode due to an unknown reason. If this is the case, then hitting F11 should solve the problem temporarily. If it starts again in full screen mode, then delete the file *localstore.rdf* in your Firefox profile directory, which is under *~/.mozilla* (to see it you need to hit CTRL+H while browsing your home directory).

---

### Post by elleppahc on 2009-05-11
Tried F11 this worked as stated.
Removed file and this worked, but lost my bookmarks.
Thanks for your help

---

### Post by lovinglinux on 2009-05-11
> **elleppahc said:**
> Tried F11 this worked as stated.
Removed file and this worked, but lost my bookmarks.
Thanks for your help

Strange, because the bookmarks are stored on another file. Anyway, you can restore your bookmarks from automatic backups. Open the bookmar manager, click the "Import and Backup" button, then select the date you want to restore.

---

