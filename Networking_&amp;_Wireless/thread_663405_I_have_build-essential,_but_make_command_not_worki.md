---
title: "I have build-essential, but make command not working"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by SandyKhan on 2008-01-10
I have *build-essential* package, but there is still a problem with **make** command. When I run it in a directory, it shows following message:

mudassar@javaDev-1:~/Desktop/gwget-0.99$ make
make: *** No targets specified and no makefile found.  Stop.

When I explicitly specify a make file, the following message appears:

mudassar@javaDev-1:~/Desktop/gwget-0.99$ make Makefile.in
make: Nothing to be done for `Makefile.in'.

Same message appears for all other files.

And, if I run **install** with **make**, it shows:

mudassar@javaDev-1:~/Desktop/gwget-0.99$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.

Guide me how to use **make** in this scenario.

---

