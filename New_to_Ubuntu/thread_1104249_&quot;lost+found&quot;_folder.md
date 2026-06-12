---
title: "&quot;lost+found&quot; folder??"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by OllieGab on 2009-03-23
In my File System I have a folder - which is crossed over - called 'lost+found'. I can't open it or read it.
Properties just says 'un-readable'.
What is it? And why can't I access it?

Ollie

---

### Post by SunnyRabbiera on 2009-03-23
> /lost+found

A windows user might mistake this directory for Linux's version of the Recycle Bin, however, beware that Linux does not actually keep any of your deleted files. Some Window Managers, like Gnome or KDE will do that for you, however, if you delete a file in a linux shell it is as good as gone. Having cleared this up, this is a directory where Linux keeps the files that it restores after a system crash or when a partition hasn't been unmounted before a system shutdown. Thus, it can recover files that otherwise would have been lost.

source:

[http://www.goitexpert.com/entry.cfm?entry=A-guide-to-Linux-directory-structure--Part-One](http://www.goitexpert.com/entry.cfm?entry=A-guide-to-Linux-directory-structure--Part-One)

---

