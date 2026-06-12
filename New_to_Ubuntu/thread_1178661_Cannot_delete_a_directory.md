---
title: "Cannot delete a directory"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by gatorbrit on 2009-06-04
I did a grsync to sync my HD with an external USB drive that is formatted NTFS.   I got some errors, which seemed to be because I had deleted several folders on the internal drive and they still existed on the external drive.

Now I have a new directory on the external drive called "results.log".
This used to be a text file and has some how be written over as a directory.

When I list the dirs I get this..


```
 
ls -d results.log
results.log

```

So i type this
```
rmdir results.log
```
and I get this
```
rmdir: failed to remove `results.log': No such file or directory

```

I also tried just deleting as a file with no luck either.



So first, I'd like to get rid of this file/dir.  Second, why does grsync produce this error?

thanks

---

### Post by aparigraha on 2009-06-04
Don't know how, but the same kind of thing happened to me on an NTFS drive - a file became a directory. I had to change permissions and/or user of the the parent folder and everything it contained. Not related to grsync in any way though.

---

### Post by dje on 2009-06-04
I also tried to use rsync to a NTFS formatted drive and wierd things happened (can't remember exactly what though). My advice would be to add an ext3 partition to the drive or completely reformat it as ext3 using gparted

dje

---

### Post by gatorbrit on 2009-06-04
> **dje said:**
> I also tried to use rsync to a NTFS formatted drive and wierd things happened (can't remember exactly what though). My advice would be to add an ext3 partition to the drive or completely reformat it as ext3 using gparted

dje

I am thinking of doing that.  I have pretty much switched 100% to ubuntu, and this NTFS drive is a sort of last holdout!   But it drives me nuts that i get screwy things from grsync with it.

I think I'll create a ext3 on it now.

FWIW, I also ran nautilus in sudo, and got told that the dir didn't exist when I tried to delete it. 

thks

---

