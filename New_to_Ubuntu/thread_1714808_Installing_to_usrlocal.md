---
title: "Installing to /usr/local"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by munja on 2011-03-25
Hello,

I would like to install all software to /usr/local. When I'm using Synaptic Package Manager or Ubuntu Software Center all the software is installed to /usr. How can I change that?

I've seen thread [http://ubuntuforums.org/showthread.php?t=33750](http://ubuntuforums.org/showthread.php?t=33750) but it dosen't actually answer the question.

Thanks for any help.

---

### Post by SeijiSensei on 2011-03-25
The short answer is that if you're installing from the repositories, user binaries will end up in /usr/bin, libraries in /usr/lib, etc.  That's pretty much [standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for all distributions.  

Moreover if you were to move the binaries manually to /usr/local/bin, etc., you wouldn't be able to update them from the repositories.

Perhaps you should tell us why you want to do this?  /usr/local is designated as the place for software you build or install yourself outside the repository structure.  What purpose would moving all the binaries serve?

---

### Post by munja on 2011-03-26
Ok. it's just that I didn't make the /usr/ partition big enough because I was expecting every new software would be installed to /usr/local which is on a separate parition.

---

### Post by srs5694 on 2011-03-26
Your best bet is to resize your partitions. You can do this with GParted, but you'll probably have to use a live CD boot to get this to work, since GParted won't resize any partition that's currently in use (such as whatever your current root (/) partition is). Also, backing up important data before resizing is wise; partition resizing operations are always inherently a bit risky.

---

