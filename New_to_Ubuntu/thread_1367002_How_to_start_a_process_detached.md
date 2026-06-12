---
title: "How to start a process detached?"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Ugluk on 2009-12-29
How can I start a process from a shell so that parent shell process would continue and terminated before child process exit?

---

### Post by x33a on 2009-12-29
could you please be more clear?

from what i understand, gnu screen might be of interest to you.

it let's you close the terminal (detach), but the processes inside it can keep running.

[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

---

### Post by lavinog on 2009-12-29
you should be able to end the line with a **&**
There is also **nohup**

screen is handy if you want to return to the shell (great for ssh connections)

---

