---
title: "Libartskde.so.1"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Warpnow on 2009-05-05
kmuddy: error while loading shared libraries: libartskde.so.1: cannot open shared object file: No such file or directory

Well, upgraded to Jaunty, and tried to install a program called Kmuddy, a KDE app for playing text based games. Many dependencies were not available, so I found them in the old intrepid repos on packages.ubuntu.com and installed them there, then installed the .deb of the file.

Then I get the above error message when I try and run the program.

Any idea how to fix it?

---

### Post by Zorg-it on 2009-06-25
Try compile the sources with ./configure --without-arts option.

---

### Post by Zorg-it on 2009-06-25
Mind that on jaunty it's better to compile kmuddy-1.0rc2 directly...would avoid a waste of time.

---

