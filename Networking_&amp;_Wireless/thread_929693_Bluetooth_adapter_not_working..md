---
title: "Bluetooth adapter not working."
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by 01000111 on 2008-09-25
I have a Belkin F8T012 USB bluetooth adapter and can't get it to work.  According to: 

[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/140511]("https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/140511")

this was fixed in 2.6.24-17.31, and I'm running 2.6.24-21.

I've also tried the blacklist and modules fix as described in the 6th entry on that same page, but whenever I plug in the adapter, it is still recognized as an ethernet adapter, not a bluetooth adapter.

Help!?!?!?!


Attached is a file containing lsusb, lsmod, blacklist and modules


Thanks in advance,
Binary-G

---

### Post by parmstro on 2008-10-28
ditto, blacklist pegasus used to work for me in 8.04, now the blasted USB bluetooth adapter is always shown as an ethernet adapter. My apple wireless keyboard is gathering dust.....

---

### Post by FrankVdb on 2008-11-16
Had the same problem with a Belkin F8T016 adapter and found a hack here:
[https://wiki.edubuntu.org/F8T016](https://wiki.edubuntu.org/F8T016)

Hope that helps. I found it very annoying too.

---

