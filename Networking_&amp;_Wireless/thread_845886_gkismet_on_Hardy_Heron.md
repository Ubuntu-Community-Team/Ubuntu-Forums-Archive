---
title: "gkismet on Hardy Heron"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by jruijgrok on 2008-07-01
Hello, I try to install gkismet on Hardy Heron but I fail to get the Gnome Perl libs right. Whatever I try to install: no succes. Perhaps I should downgrade to previous Ubuntu version....
Anyone succesful in installing gkismet on Hardy?
Thanks, Jaap

---

### Post by waterpile on 2008-07-01
I've spent a while trying to get gkismet to work as well, with no luck.
Same problem as here: [http://ubuntuforums.org/showthread.php?t=26660](http://ubuntuforums.org/showthread.php?t=26660)
I can't find libgnome-perl for hardy.  I have the libgnome2-perl package but can't get gkismet to work with it

---

### Post by Digital Viking on 2011-04-12
I'm a few months into Linux as a whole, and Ubuntu specifically.

I ran into the same problem in maverick. Apparently the new gnomelib-perl lists everything as "Gnome2" and "Gtk2". Had to go through every .pm file in GKismetApplication.pm and change "use Gnome;" to use Gnome2" (same with "use Gtk"). Simple and stupid, but so bloody tedious! This solution, however, seems to lead to a new problem:

raeven@AlumiBox:~$ gkismet
Can't locate object method "init" via package "Gnome" at /usr/local/lib/gkismet/GKismetApplication.pm line 63.
raeven@AlumiBox:~$ 

In this, the Great and Mighty Google has failed me! Who's got the next workaround?

---

