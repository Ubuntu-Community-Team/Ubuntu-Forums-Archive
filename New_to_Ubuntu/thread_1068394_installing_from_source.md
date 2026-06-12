---
title: "installing from source"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by aap21956 on 2009-02-12
As I understand the process, installing from source requires these three commands:  ./configure ; make ; make install.

I'm just curious why the last command is make install and not just install since the make command has already been issued in the second step.  Thanks!

---

### Post by snova on 2009-02-12
First point: That series often works, but not always. It depends on the build system the software uses, though Autoconf/Automake is perhaps the most common.

Second point: **make install**, if you're installing to the default location of /usr/local, needs administrative priviliges to write there. Thus it is **sudo make install**.

Now, the answer. :)

make is a build tool, it decides when files have changed and only rebuilds the ones that have. make without arguments will build the default target, which is the program itself. **install** is just another target- albeit one that doesn't actually build anything, but instead does the obvious thing.

There is an install command, but it serves a different purpose- basically a file copier that sets permissions on the destination file automatically.

---

### Post by aap21956 on 2009-02-15
Thank you for the clarification and detailed response.

---

