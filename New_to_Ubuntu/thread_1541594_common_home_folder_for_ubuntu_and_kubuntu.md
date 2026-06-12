---
title: "common home folder for ubuntu and kubuntu?"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by jfreak_ on 2010-07-29
currently I have ubuntu with separate / and /home. when I install kubuntu can I use the same /home for it?
Otherwise it would be a pain to mount it everytime I login

---

### Post by Paqman on 2010-07-29
Yes, just make sure to create a separate user account so they don't get mixed up.

Having said that, you can install both KDE and Gnome on the same system, with the same user and it works reasonably well, so you could just do that. All you need to do to install KDE is install the package kubuntu-desktop, then log out and pick a KDE session instead of a Gnome one when you log back in.

---

### Post by jfreak_ on 2010-07-29
yeah but that loads the gnome environment with KDE clutter. I intend to retain the gnome as the main workhorse and KDe when i need a change.

I'll be able to share music and videos without any work-arounds right?

---

### Post by nothingspecial on 2010-07-29
It will work fine for (K)Ubuntu, it is when you have completely different linux distros it becomes a problem.

A much better solution for running both than doing it on the same partition imo

---

### Post by Paqman on 2010-07-29
> **jfreak_ said:**
> yeah but that loads the gnome environment with KDE clutter.


Indeed it does, although you could clean up the menus relatively easily. Just because something is installed doesn't mean it *has* to have a menu entry.

> 
I'll be able to share music and videos without any work-arounds right?

Of course. Data is data.

---

### Post by oldfred on 2010-07-29
With multiple installs I prefer a separate /data partition. Then you can mount that in as many installs as you want with linking and/or fstab. Data is data and does not change.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

