---
title: "[SOLVED] Help installing zsnes"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Drubie on 2009-01-05
I am trying to install zsnes, and am stuck at the first step (per the instructions in the readme file)

the instructions say:
./compile
make
make install

pretty standard.

however, I am stuck at the ./compile step. It keeps stopping with an error:
[INDENT]configure: error: a curses library is required to use the debugger[/INDENT]
it looks for initscr in lcurses, lncurses, and lpdcurses, and does not find them.

The problem is: Do I need to install some package?  If so which?

Thanks in advance

---

### Post by fenian on 2009-01-05
You need to install libncurses5-dev and initscripts ,search for them in synaptic and install them.

---

### Post by Drubie on 2009-01-05
thanks, I just needed the name of tha package.

yay, it worked!  Thank you!

lol:
Configure complete, now type 'make' and pray.

---

