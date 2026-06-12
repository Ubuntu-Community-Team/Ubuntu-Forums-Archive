---
title: "External Drive Terminal Help"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by sebadoh86 on 2009-06-23
Hello everybody. I'm new to linux and it's my second day using it's interface. I've been trying to study terminal scripts and so i can get the full effect of linux. Well, i'm stumped with a problem. I finally got my external drive to mount to the media folder. The problem is that I can't access it through the terminal. I would like to access it so i can edit some of the files instead of having to go through all the folders. This is my terminal output:


dave@Dave:~$ cd /
dave@Dave:/$ cd media
dave@Dave:/media$ ls
cdrom  cdrom0  floppy  floppy0  force [COLOR=black]FreeAgent Drive[/COLOR]  ZIP-100
dave@Dave:/media$ cd FreeAgent Drive
bash: cd: FreeAgent: No such file or directory

'FreeAgent Drive' has a dark green highligh under it, and i know that it may have limited permission to access it. I don't know if this helps but :

dave@Dave:/media$ ls -l
total 50
lrwxrwxrwx 1 root       root           6 2009-06-19 10:18 cdrom -> cdrom0
dr-xr-xr-x 4 4294967295 4294967295   136 2009-06-09 20:45 cdrom0
lrwxrwxrwx 1 root       root           7 2009-06-19 10:18 floppy -> floppy0
drwxr-xr-x 2 root       root        4096 2009-06-19 10:18 floppy0
drwxr-xr-x 2 root       root        4096 2009-06-19 16:00 force
drwxrwxrwx 1 root       root       24576 2009-06-21 22:39 FreeAgent Drive
drwx------ 7 dave       root       16384 1969-12-31 18:00 ZIP-100
dave@Dave:/media$ 


Thanks for the help everyone!

---

### Post by frup on 2009-06-23
when there is a space in the terminal you need to put the argument in quotes.

cd "FreeAgent Drive"

should allow you to move to that directory.

Also try typing cd Free and then pressing tab and see what happens.

---

### Post by sebadoh86 on 2009-06-23
> **frup said:**
> when there is a space in the terminal you need to put the argument in quotes.

cd "FreeAgent Drive"

should allow you to move to that directory.

Also try typing cd Free and then pressing tab and see what happens.

Thank your Frup! it worked!

---

