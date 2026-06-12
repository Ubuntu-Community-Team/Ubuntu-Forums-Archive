---
title: "GTK and glade compilation errors"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by anewguy on 2009-01-24
I use the following line in a shell script to compile my program:

gcc -Wall -g -o cvsutil_gtk a_start.c `pkg-config --cflags --libs gtk+-2.0 libglade-2.0` -lusb


This worked fine, even with 8.10, until I had to delete the Ubuntu desktop a while for work reasons.  Now that that part-time temp job is over, I re-installed Ubuntu 8.10 and let it go through the updates - about 250+ of them.  Rebooted when requested a long the way.  Then added the GTK development libraries and glade development libraries via synaptic package manager.  I noticed it says libglade-2 is a dummy package since glade 3 is now in the repositories.  However, even with libglade-2 installed, I get errors in compilation saying libglade-2.0 couldn't be found, and it also can't find the include <gtk/gtk.h>, all of which worked before when I had 8.10 installed.

So can anyone help a dumb guy out and tell me what I've missed, what package(s) I might need to install?

Thanks in advance!
Dave :)

---

### Post by anewguy on 2009-01-24
Any help or ideas would be greatly appreciated!  I assume 1 or more of the packages has changed, so the libs I am pointing at are no longer valid, but where do I point them to now?

Dave :)

---

### Post by anewguy on 2009-01-25
Solved - wasn't actually using glade, so just removed the reference in the pkg-config info.

---

