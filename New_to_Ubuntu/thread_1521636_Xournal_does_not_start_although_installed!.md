---
title: "Xournal does not start although installed!"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by ninos on 2010-07-01
I installed Xournal on **Edubuntu 10.04**, and it failed to start.
Then, I removed it and re-installed it, but to no avail.
When I tried to start it from the terminal
I received the following message:

emmanouil@emmanouil-laptop:~$ xournal

** (xournal:1550): CRITICAL **: menu_proxy_module_load: assertion `dbusproxy != NULL' failed
Segmentation fault
emmanouil@emmanouil-laptop:~$ 

Any ideas on how I can fix this critical error?

**Xournal** is a very useful educational app
[ free software (GNU GPL) and runs  on Linux (recent distributions) and other GTK+/**Gnome** platforms]
that I use on another computer at school
on Ubuntu 9.10,
and it works fine there.

---

### Post by lkjoel on 2010-07-01
Check this website out.
It has all the dependencies, the package itself, and the sourcecode
[http://packages.ubuntu.com/lucid/xournal](http://packages.ubuntu.com/lucid/xournal)

---

### Post by ninos on 2010-07-17
The problem was fixed, a few days ago, after installing the recommended updates.
The new Linux kernel.
Now Xournal works fine.:KS

---

