---
title: "undo command?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by intense.ego on 2008-12-13
I tried backing up my home folder before installing intrepid using rsync, but it seems to have copied the files to the home folder again instead of to my external hard drive. Now, my /home is full (it had 2gb free previously) and I want to know if there is anyway of undoing or reverting the previous command, so that I could free up that space again.

With regards to the backing up, I'll just copy and paste it this time to avoid any problems. Also, if there are two copies of the same files, is that any hindrance to system performance? (i.e. will a system not know which file to access?)

Thank you

---

### Post by Paqman on 2008-12-13
Just delete the extra copy of the files.

---

### Post by JohnFH on 2008-12-13
In theory having copies of the same file should have no effect on system performance, unless you have completely run out of disk space.  However some applications may search a directory for certain file types and those applications could end up with twice the amount of data needed.

Look at the manual page for rsync instead of copy and paste - it's well worth it.   

As for an undo command, no, there isn't one unless you already have a backup.  Are there a lot of files in your home directory?  Would it be a pain to delete the duplicates manually?

To find out which files are taking the most space in your home directory:
```
 du | sort -n
```
The largest duplicates are the ones I would get rid of first.

---

### Post by intense.ego on 2008-12-13
I would have deleted the duplicates manually, but I don't know which files were duplicated. Nevermind, it shouldn't really be a problem like you said. Thanks for the help though.

---

### Post by oldos2er on 2008-12-13
The program fslint can find duplicates, and other "file system lint".

---

