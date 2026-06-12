---
title: "installing Simple Linux Backup"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by lee292 on 2009-03-04
I recently downloaded a Linux backup utility called Simple Linux Backup from SourceForge.net.  The file is in a gzipped tar format. Filename is simplelinuxbkup-0.3.3-i386.tar.gz. What's the secret to installing it?  I would attach it but at 2.5 Mb it's too big!

---

### Post by hexanol on 2009-03-04
Well, first, you need to unzip and untar it! :D

```
tar -xvzf simplelinuxbkup-0.3.3-i386.tar.gz
```

Then there's going to be some instruction in the new folder created by tar, and you might have to install some dependencies before compiling the source code...

---

### Post by Temposs on 2009-03-04
hi lee,
   Try getting simple backup from the repositories. It's a newer version, anyway. Just open the Add/Remove program and search for "simple backup".

In general, try to find your programs through the Add/Remove application first. Ubuntu will keep them updated. If you download them from the web, they won't be updated.

---

### Post by lee292 on 2009-03-04
Tried add/remove, did the search and it's not listed.  Do I need to tweak Add/Remove to look for apps from SourceForge?

---

### Post by Temposs on 2009-03-04
Add/Remove doesn't look for apps from Sourceforge. It has a list of programs that the Ubuntu people keep updated or endorse.

When you open Add/Remove, it says "Show:" at the top with a drop down next to it. Make sure "All Available Applications" is selected. Then try searching backup and see what comes up. There should be several backup programs. I use Simple Backup.

---

### Post by UbuntuNerd on 2009-03-04
check out this [LINK](http://my.opera.com/ubuntunerd1/blog/h-5)

---

### Post by cariboo on 2009-03-04
In Add/Remove search for sbackup, or use the search button in System-->Administration-->Synaptic Package Manager.

Jim

---

### Post by iBurger on 2009-03-05
Will this utility backup my complete Ubuntu installation?
> I'm using Norton Ghost now, but I think that there are smarter ways.

---

### Post by magump on 2009-03-05
Are you looking for a program that will make an image of your drive or Ubuntu partition so that you can quickly restore your system to a previous session?

---

### Post by lee292 on 2009-03-05
My bad!  As they say, "If all else fails, read the instructions!"  The instructions for installation were under the "Download" button on the web page.  SORRY!

---

### Post by lee292 on 2009-03-06
> **Temposs said:**
> Add/Remove doesn't look for apps from Sourceforge. It has a list of programs that the Ubuntu people keep updated or endorse.

When you open Add/Remove, it says "Show:" at the top with a drop down next to it. Make sure "All Available Applications" is selected. Then try searching backup and see what comes up. There should be several backup programs. I use Simple Backup.

You had the right idea!  I went through "Show" and found "All Open Source Applications" and found it.  Installed perfectly!  Thanks!

---

