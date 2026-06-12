---
title: "cammnad line issue: run program"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by 3l3vans on 2009-04-19
i have been learning C from a book as of late and i ran into a strange problem today that i am not even sure how to phrase the question. i WAS using SUSE 11.1 and having no problem creating code, compiling it in GCC, and then running each program by typing its name. NOW i have switched to Xubuntu (because it rules!) and i am having a problem.
     I use NANO to code, just like i did in SUSE, and i use GCC to compile just like i did in SUSE. GCC gives me no errors, but when i type the name of the program i get "command not found". YES i am in the right location when trying to run said programs and it happens with the both the code i created in SUSE and the code i have created since i switched. I have checked the permissions of said files and they all belong to my current user in Xubuntu. I checked to make sure they were marked "executable" and they are.
     Am i just missing a package? Is there a run command for this version of bash that i am using? i dunno. here are my specs:

bash -version=

GNU bash, version 3.2.39(1)-release (i486-pc-linux-gnu)
Copyright (C) 2007 Free Software Foundation, Inc.

gcc -version=

gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

i don't think my hardware is important in this case but i am on an eeepc 900ssd. any info on where to look would be grand, thanks 3l

---

### Post by doas777 on 2009-04-19
well, when I want to run a script/app from the directory I am currently in, I always add ./ to the begining of the app name.
eg```
./a.out
```

---

### Post by 3l3vans on 2009-04-19
THANK YOU that did the trick...i guess it just wasn't required in my previous version of bash...cheers! 3l

---

### Post by 3l3vans on 2009-04-19
now how do i mark this thing solved? :)

---

### Post by glotz on 2009-04-19
The functionality is broken at the moment, so you can't.

---

### Post by anewguy on 2009-04-19
Just go to your first post, click edit, then click the advanced button.  This will allow you to edit the title - just add [SOLVED] to the front of the title and save it.

Dave :)

---

