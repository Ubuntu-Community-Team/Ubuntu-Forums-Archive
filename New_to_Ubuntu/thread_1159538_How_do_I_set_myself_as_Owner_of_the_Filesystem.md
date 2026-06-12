---
title: "How do I set myself as Owner of the Filesystem?"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Missing_Number on 2009-05-14
I want to install the Ubuntulooks engine by pasting things into a specific folder on my filesystem.  The problem is, I'm not allowed to do so because I'm not the owner.  How to I make myself the owner of the filesystem or at least the specific folder I want to paste stuff into?

I'm using Wubi to dual-boot my hard drive with Windows XP and Ubuntu.

---

### Post by Ocxic on 2009-05-14
You don't, the file system and contents are and must be owed as root. what you would want to do is hit "alt+f2" and type in "gksu nautilus" that will give you a root nautilus windows that will allow you to make changes to you main file system.

---

### Post by Missing_Number on 2009-05-14
Thanks man.  I'm yet another Windows refugee trying out Ubuntu for the first time.  I wanted to change the theme.

---

### Post by albinootje on 2009-05-14
> **Missing_Number said:**
> Thanks man.  I'm yet another Windows refugee trying out Ubuntu for the first time.  I wanted to change the theme.

Welcome to Ubuntu! :)

For adding new themes for the Gnome desktop (the default desktop in Ubuntu) you can do the following :
1) -> System -> Preferences -> Appearance -> Theme
(Or right click on the desktop, choose "Change Desktop Background", then click on Theme)
2) drag and drop the downloaded theme file (.tar.bz2) into that.

---

