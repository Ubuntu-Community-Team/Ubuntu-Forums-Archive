---
title: "an absolute beginner question"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by chasenblues on 2009-08-09
Hello all...Hopefully some one can point me in the right direction.
I ordered the ubuntu os and recieved the cd and tried to install it "inside" my windows Vista home premium 32 bit os.  My computer is a HP compaq CQ50 notebook pc.
it has an AMD anthlon dual-core QQL-60 1.90 GHz.
it installs to a certain point then i get an error message saying permission denide check log file such and such, When i checked the log file the only error message i saw was this     IOError: [Errno 13] Permission denied
can some one help a brother out .
the version of ubuntu i have says its
Ubuntu 9.04
desktop edition.
 
will this version install and work on a Laptop.(i have a feeling it won't)
and is there a version that is put out exclusively for laptops?
 
Thanks

---

### Post by mevets on 2009-08-09
Judging from the term "inside" that leads me to believe you are trying to use the wubi installer (trying to install while running windows). If so I think this IO error means you dont have enough space on your hardrive. Could that be it?

---

### Post by esalnoj on 2009-08-09
Jaunty 32-bit (desktop) runs just fine on my gateway laptop.

The only differences in versions you get with ubuntu are amd64, 32-bit, server, netbook, and EEE editions. Besides the desktop managers of course (KDE, gnome, xfce).

When you boot the CD, run the "check disk for errors" option.

---

