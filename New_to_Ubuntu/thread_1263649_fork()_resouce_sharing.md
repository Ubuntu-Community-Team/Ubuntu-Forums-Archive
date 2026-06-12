---
title: "fork() resouce sharing"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by polarbear12345 on 2009-09-11
suppose i have a program P1 in which i have opened a file f1
Then i give fork()command.

Will the child process created share the same parent file f1 also.
or
will the child process make a copy of above file with same contents.
or
no file will be there in child process

---

### Post by freak42 on 2009-09-11
how about you try it out?

hth

---

### Post by Penguin Guy on 2009-09-11
Unless you have specifically designed it to do anything special, then it won't - it will just use the same file.

---

