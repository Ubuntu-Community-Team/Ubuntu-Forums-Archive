---
title: "Running .bat files"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Ranko95 on 2009-04-26
Is there a way to run .bat files on ubuntu?? I don't really want to learn python so I'm looking for a program. Thanks!

---

### Post by fdrake on 2009-04-26
[link]("http://ubuntuforums.org/showthread.php?t=477222")

---

### Post by anim on 2009-04-26
Download DOSBOX. Its in the repositories.

in DOSBOX you have to mount the folder your files are in:

mount c \home\usr\

Run your batch and you are good to go.

---

### Post by sgosnell on 2009-04-27
.bat files don't run natively, but script files do.  They're pretty much the same thing, but even more capable.  The name and extension don't really matter, you just need to set the executable bit and they'll run.  There is a way to do everything a .bat file will do, but some of the commands are different.

---

