---
title: "Viewing Ubuntu file system from Windows"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by Sholto on 2010-07-18
[SIZE=3]I previously posted about viewing my Ubuntu file system from Windows when the two systems are on different machines.  However I have now created a dual boot on a single machine and would like to see my Ubuntu shares from Windows.  Currently I can see my Windows shares from Ubuntu (on the same machine, and from different machines), and I can see my Ubuntu shares from Windows, when they are on different machines.
However what I can't do is see my Ubuntu shares from Windows when both are on the SAME machine.  This can't be an issue of ext4 format, or I would not be able to see Ubuntu files on a different machine.
Anyone have any ideas?  Er...please!
[/SIZE]

---

### Post by migs73 on 2010-07-18
I think it will be the format!  When you look into another machine the host OS (Ubuntu in this case) will be running and will present the files (share them) in a way that can be read by other systems. When you dual boot only the windows OS is operating and it cannot read the ext formatting of the Ubuntu files.
I believe you can read from ext formated partitions using special software in windows but know little about it.

---

### Post by HermanAB on 2010-07-18
[http://www.linuxjournal.com/article/9449](http://www.linuxjournal.com/article/9449)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by migs73 on 2010-07-18
Thanks Herman

Now I know a bit about it!!!

I knew it existed but had no reason to look into it further.

Migs :D

---

### Post by Mark Phelps on 2010-07-18
Understand, though, that you still will NOT be able to access the Ext4 filesystem from Windows on the same machine.  Ext4 support (as far as I know) has not yet been added to those utilities.

---

### Post by Arla on 2010-07-18
Make your Ubuntu Shares NTFS, then it will work (or FAT32).

---

### Post by Sholto on 2010-07-18
Thanks fellas,
Herman, the article is a bit dated and only claims LTOOLS will work with Ext3, and Ext4 is still questionable (see Mark's contribution).
Arla - how do I convert the Linux shares to NTFS?  There doesn't seem to be a way to do this in the Folder Sharing window in Linux.

---

