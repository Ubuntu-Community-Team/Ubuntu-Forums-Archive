---
title: "Tar files problems"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Captain Lightning on 2010-09-02
Hi all,

What I am aiming to do is set up cron backups of a few types of files in directories, such as .cpp files in my programming directory, and this is easy for the most part.

Although, I have an issue with tar, I am trying to have a .tar file on my backup disk that has only the .cpp files in it, and I don't want to have to navigate through many files to get to these cpp files (the files i want to backup have long paths)

After reading tar man page, i see the -C option is quite handy, but doesnt go far enough.

For example, this is the guessed command i attempted:

> tar -cvf /media/backupusb/prgrm.tar -C /home/myname/myprogram/ *.cpp

and I get the error > tar: *.cpp: Cannot stat: No such file or directory

this is strange because if i changed into the directory first and then ran tar -cvf prgrm.tar *.cpp it works, and isnt this the same thing?

---

### Post by SlugSlug on 2010-09-02
try it without the -C

---

### Post by bredman on 2010-09-02
I must admit that your command looks OK, and I don't know why it doesn't work.

However, here is an alternative method to do the same thing...

cd /home/myname/myprogram/; /bin/tar -cvf /media/backupusb/prgrm.tar  *.cpp

Note that I used the fully-qualified name for tar because cron expects fully-qualified command names.

---

### Post by Captain Lightning on 2010-09-02
Thanks for /bin/tar tip,

But yes that does work, although it would be good to find out if I could get the -C command do work the way I wanted

---

