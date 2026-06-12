---
title: "Clustering two ubuntu servers"
date: 2019-09-18
forum: Networking &amp; Wireless
---

### Post by jeffrey1012 on 2019-09-18
Hi,

I have very CPU intensive tasks that take forever and I would like to spread the tasks among several machines. I read about Beowulf, but it seems there is little activity or new posts for "Ubuntu Beowulf". Is there some Ubuntu package to offload some of CPU intensive tasks to another server? Most of the tasks are executed from shell, so for now I am torturing rsh, but there must be better ways to do it. 

Does anyone know of an easy to install package that would allow me to offload some of shell executed commands to another Ubuntu server?

Thank you!

---

### Post by TheFu on 2019-09-19
Don't use rsh. Use ssh.

There's a number of packages that can help with batch processing.  batch, at, xargs, taskspooler, gnu-parallel.
[https://www.gnu.org/software/parallel/](https://www.gnu.org/software/parallel/)
[https://www.gnu.org/software/parallel/parallel_alternatives.html](https://www.gnu.org/software/parallel/parallel_alternatives.html)
A quick google search found at least 50 different possible options.
I use xargs with find. Also use taskspooler about 50x a day.  Sometimes inotify is really all I need.

---

