---
title: "Help with saving a C program"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by F1r3st0rm on 2010-10-14
Hello, I am having trouble making an executable C file after I compile it save to my USB and not under my /usr/bin directory. Any help?

---

### Post by GregBrannon on 2010-10-14
More info would be helpful.

Verify that the program runs fine before you move it.  Maybe it's a path problem, but it's hard to tell with the info you've provided.

What kind of trouble?  If you're getting error messages, post them.

Are you trying to run the same executable on the same machine just from the different location, or are you moving it to another machine and then trying to run it?

---

### Post by anewguy on 2010-10-14
Do an "ls -al" on the file on the USB stick - it probably is rw- e.g. not executable.  Just do a chmod to executable to it or do it via "places" and "properties".

To execute:  ./filename.extension



Dave ;)

---

### Post by F1r3st0rm on 2010-10-17
> **GregBrannon said:**
> More info would be helpful.

Verify that the program runs fine before you move it.  Maybe it's a path problem, but it's hard to tell with the info you've provided.

What kind of trouble?  If you're getting error messages, post them.

Are you trying to run the same executable on the same machine just from the different location, or are you moving it to another machine and then trying to run it?

The program works fine and I'm just trying to save the executable on USB stick

---

### Post by F1r3st0rm on 2010-10-17
> **anewguy said:**
> Do an "ls -al" on the file on the USB stick - it probably is rw- e.g. not executable.  Just do a chmod to executable to it or do it via "places" and "properties".

To execute:  ./filename.extension



Dave ;)

Errr, What's a chmod and an ls -al?

---

