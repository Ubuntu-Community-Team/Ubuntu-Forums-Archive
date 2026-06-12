---
title: "what is the best backup software for ubuntu, apart from command line rsync"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by legolas_w on 2010-04-30
Hi,

I am looking for a GUI application to help me create incremental backup of my data from my hard disk to external hard disk.

So far I was using lucky backup, is there anything better than that?


thanks.

---

### Post by Temposs on 2010-04-30
The best one in my opinion is deja-dup. It is in the Ubuntu repositories for you to download with Ubuntu Software Center

---

### Post by Drock on 2010-04-30
I use [back in time]("http://backintime.le-web.org/")

---

### Post by ugm6hr on 2010-05-01
rsync is very good - I used to use grsync (rsync + GUI) - but now just use rsync.

Now, I use the custom menu actions in XFCE thunar File Manager, so I can run a pre-written rsync command with the right-click menu.

---

### Post by hhoyt on 2010-06-30
You probably have the best.
Partly depends on whether you want versioning; 
If you just need incremental, LB is about as good as it gets.

also be aware there are some problems with ext4 on BIT and FreeFileSync (very fast, worth trying).

If you go with BIT for versioning, best I recall it DEFAULTS to NO hidden files (go figger).

Howard

---

