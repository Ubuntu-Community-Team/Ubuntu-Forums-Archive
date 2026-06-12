---
title: "/proc folder question"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by SlayBeau on 2010-04-18
I have been spending the morning cleaning my 16GB netbook of unwanted/unneeded files in preparation for summer fieldwork.  I need the space.

So I autocleaned, cleared out the orphaned files, etc., etc.  My HD now has .odt files, .pdf files, and a handful of photos.  That's it, and all I got left is 4GB of memory.  I thought that was weird, but maybe not.

Anyway, I started seeking files by hand and discovered 76 .jpgs in taken by Cheese.  They were kept in /proc/8461/fd/media.  I opened the filed, found all 76 .jpgs and was going to batch delete them, but they disappeared.  Not just the files, but the entire folder.  So I did a search again for a known file name (0003.jpg) and found that they had all moved to another subfolder in /proc, something like /proc/7703/fd/media.  I tried again to back out to the main subfolder to delte the whole thing and it happened again: subfolder 7703 disappeared.  I ended up manually deleting each .jpg from within Cheese.

#1  What gives?

But more importantly, what is this folder.  At the moment it holds 163 items and nearly a gig of my memory.  Exploring the folders shows a lot of empty subfolders, others with white Xs or roll-back arrows.  When I check properties, many of them contain 63 items but the volume is ominously listed as "unknown."

So what is this folder for?  What is kept here and is there any way to figure out what can be deleted.  I'm not exactly desperate for space, but from what I can figure, my documents all taken together (papers, books, articles, etc. - I'm a doctoral student) only use about 2G.  Ubuntu shouldn't take more than 4G, right?  So where the heck is the other 5+G of memory.  How do I find out?

I've already used this tutorial to clean things up a bit: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920).

Thanks for any help.

---

### Post by Didius Falco on 2010-04-18
/proc is actually a virtual file system it's sort of a window into what the kernel sees - files, directories and hardware.

If you were to boot with a Live CD and look at the /proc directory on the installed partition on your pc, it'd be empty, because that kernel wouldn't be loaded.

For your purposes, cleaning out space, you don't need to touch it.

here are a couple of links to get you started on the /proc directory and it's uses that you can peruse at your leisure:

[http://www.freeos.com/articles/2879/](http://www.freeos.com/articles/2879/)

[http://computingtech.blogspot.com/2009/09/ubuntu-directory-tree.html](http://computingtech.blogspot.com/2009/09/ubuntu-directory-tree.html)

[http://it.toolbox.com/blogs/locutus/what-does-this-proc-directory-do-17379](http://it.toolbox.com/blogs/locutus/what-does-this-proc-directory-do-17379)

---

### Post by SlayBeau on 2010-04-18
Thanks!

---

### Post by Paqman on 2010-04-18
You might want to run the Disk usage analyser as root. Hit ALt-F2 and enter:
```
gksu baobab
```
Then get it to scan your entire filesystem. It'll show you where all the cruft is.

---

