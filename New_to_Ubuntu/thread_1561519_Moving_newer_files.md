---
title: "Moving newer files"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Sysqi on 2010-08-26
I'm trying to put together a command that will let me move files from one directory to another if they are newer than the current files in the directory.  The files names are identical, as well as the directory names.

any suggestions?

---

### Post by Rubi1200 on 2010-08-26
```
man mv
```Should help :)

And welcome to the forums!

---

### Post by inameiname on 2010-08-26
Technically Grsync does that whenever you want as a way to backup files and folders. Just an option.

---

### Post by Sysqi on 2010-08-26
It's possible i'm making it harder than it needs to be.  I have a windows file server that has 2 copies of the same directory, and so I'm trying to use linux to copy over any newer files from one directory to the other.  Usually that's an easy task, but these directories have anywhere between 10-15,000 sub directories which is why I figured it would be easier to do it command based rather than trying to use windows.

I'll try maning mv.

And thanks for the welcome.  I've been only using Ubuntu sololy as my desktop for about 6 months now, but have been goofing off for the last few years.

---

### Post by Vaphell on 2010-08-26
mv -u will do what you want, -u only updates the destination file if the source file is newer

---

