---
title: "MoBlock question"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by RaceNChase on 2010-04-15
Hi,

I went to the mobloquer site and added the repo and the gpg key for 9.10 which is the version I am currently using.  When I launch the program it states it cant find moblock.log in the /var/log folder.  I found the folder but cant drag and drop an empty log file into it.  Mobloquer says that I can specify a new path but I dont see where or how.

How do i: add moblock.log to /var/log or how do i specify a new location?  Shouldn't it have put the files where it wanted them on installation?  It is being installed directly from the mobloquer repo.

---

### Post by The Titan on 2010-04-15
You are going to have to be root to add a file there.

To add an empty file in that folder simply pass this command into the terminal:
```

sudo touch /var/log/moblock.log

```

then enter your password and voila!

---

### Post by RaceNChase on 2010-04-15
that did it! thank you!

---

### Post by The Titan on 2010-04-15
No problem.

---

### Post by lovinglinux on 2010-04-15
For future questions about moblock, take a look at [General MoBlock thread](http://ubuntuforums.org/showthread.php?t=803183), which is well supported by jre.

---

