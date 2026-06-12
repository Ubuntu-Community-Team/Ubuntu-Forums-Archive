---
title: "Help Accessing Window Shares...."
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Ron Carson on 2009-12-19
First Post...  I've been using Ubuntu Karmic on/off for about 1 month. I want to make a complete shift from Windows, but I have some problems that must be solved.  Primarily, I need to be able to access a Windows' share while using a program installed via Wine. I can see the Windows' share but I can not figure out how to mount the share so that the Wine program can access it.   Is this a question for the Wine forum?

---

### Post by Paqman on 2009-12-20
You can mount a remote Windows share so that it appears as a normal folder on your machine.

You can do this on a one-off basis by navigating through Places > Network, but if you want it to mount permamently then you'll have to add an entry to the file /etc/fstab.

[How to mount Windows shares]("http://ubuntuforums.org/showthread.php?t=288534").

---

### Post by 3rdalbum on 2009-12-20
When you mount any sort of virtual filesystem in Gnome, it gets mounted to a location inside ~/.gvfs (that is, a hidden folder called ".gvfs" inside your home directory). I always add a bookmark to this folder in Gnome and KDE so it's easy to access in all programs.

In Wine, you can access your root filesystem through Z:\. You can navigate to your home directory from there.

---

