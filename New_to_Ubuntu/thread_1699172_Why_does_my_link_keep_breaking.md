---
title: "Why does my link keep breaking?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Churchwarden on 2011-03-03
Very new to Ubuntu so forgive my asking very basic question.

I have a dual boot system (Ubuntu/Vista) and am wanting to use the documents that I have already in the D: (Data) partition created in Vista.  There is a folder called Documents in which are all my windows created efforts.  I have created a link to this and put it on the desktop.  It works fine until the next reboot when the link has broken.

Is there a work around this?

What I would really like to do is to redirect the "Documents" item on the Places menu to link to my chosen folder.  I can do this in Vista.  Can it be done in Ubuntu?

TIA

Nick

Loving the speed of Ubuntu!

---

### Post by Verbeck on 2011-03-03
that could be because the partition is not set to auto mount at boot,
you'll have to either mount it every time from the places menu or write a line for that partition in /etc/fstab

---

