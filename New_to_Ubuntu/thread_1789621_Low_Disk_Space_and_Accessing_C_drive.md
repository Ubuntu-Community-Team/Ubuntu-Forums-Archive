---
title: "Low Disk Space and Accessing C drive"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by waleedaslam on 2011-06-24
I am new to ubuntu so pardon me for any stupid questions. I installed ubuntu in my C drive and during the installation, specified the size to be 3GB. Now when I run ubuntu it says low disk space. I am running it alongside windows 7, and in windows 7 my C drive has 29GB of free space. I don't know what to do.
    
Also I can't access my windows program files from ubuntu. Is there some way of accessing the programs of window program files and running them in ubuntu?

Thanking you guys in anticipation.

---

### Post by jtarin on 2011-06-24
Did you install WUBI? The Ubuntu install that you do inside Windows?

---

### Post by waleedaslam on 2011-06-24
Yes, I used wubi and installed it inside windows.

---

### Post by jtarin on 2011-06-24
> Can I force Wubi to install even if I have less than 5GB of free disk space?

Yes; start Wubi with the argument "--skipspacecheck". Be aware that 3GB of space is required as a minimum, though, as well as enough space to store the ISO. Pushing this limit too hard may cause errors. [From here.]("https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c")

---

### Post by 3rdalbum on 2011-06-24
3GiB is too small for Ubuntu. You should remove Ubuntu using Windows' "Add Remove Programs" and install it again in Wubi with more space (10 gigs is a realistic minimum for a beginner), or go the whole hog and do a real dual boot install of Ubuntu by booting your computer from the CD.

When you have used Wubi, the Widows drive is under the /host directory in the Filesystem. When you do a real dual boot install, it appears in the Places menu, the Launcher at the side or the sidebar of the file manager.

---

### Post by Rubi1200 on 2011-06-24
As 3rdalbum pointed out, 3GB is too small.

However, one option is to resize the Wubi install to get that extra space you need:
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by waleedaslam on 2011-06-24
Thanks

---

