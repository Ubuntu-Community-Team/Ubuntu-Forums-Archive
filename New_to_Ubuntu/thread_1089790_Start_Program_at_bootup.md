---
title: "Start Program at bootup"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by bj218 on 2009-03-07
How can I have my Password Mgr. Program (keepassx) start at bootup?

---

### Post by itisbasi on 2009-03-07
Go to system preferences>sessions and add the program to your startup list.

---

### Post by thtrgremlin on 2009-03-07
verbose directions  :)

---

### Post by bj218 on 2009-03-12
> **itisbasi said:**
> Go to system preferences>sessions and add the program to your startup list.

I did this and it did not work. In the Startup lst Window I clk ADD then in 
the next window for the Name I entered Keepass for the Command I entered
Keepassx. Now if I go to Preferences Sessions Startup lst This now appears in the starup lst. What do I do now!!

---

### Post by cbtengr on 2009-03-12
> **bj218 said:**
> I did this and it did not work. In the Startup lst Window I clk ADD then in 
the next window for the Name I entered Keepass for the Command I entered
Keepassx. Now if I go to Preferences Sessions Startup lst This now appears in the starup lst. What do I do now!!

It worked for me by adding "/usr/bin/keepassx" in the Command box rather than just keepassx.

---

### Post by bj218 on 2009-03-13
> **cbtengr said:**
> It worked for me by adding "/usr/bin/keepassx" in the Command box rather than just keepassx.

I first made the change "/usr/bin/Keepassx" then I did a restart it did not
work. I then changed the capital K to a lower case k but this I did a shutdown and turned off pwr. for 30 sec. and on startup Keepassx started.
Thanks much you made it work for me. This is really a great Forum for people like me just starting to learn Linux.

How do I mark this thread SOLVED?

---

