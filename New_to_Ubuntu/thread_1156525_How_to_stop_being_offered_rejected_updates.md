---
title: "How to stop being offered rejected updates?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by bettyhills on 2009-05-11
Is there a way to stop Update Manager from repeatedly offering the same updates over and over again? Said another way...  Is there a way to reject an update once and for all, or at least until you change your mind and go seeking it?

---

### Post by benerivo on 2009-05-11
There is a 'pin' system as part of the apt package management system that ubuntu uses. It can control the way packages are uprgraded. I used this a couple of years ago, but can't really remember enough to say how to do it, but this page should help you out (see section 3.10)...
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

PS - I did this in a debian system, but i'd guess this should work the same for ubuntu.

---

### Post by Dill on 2009-05-11
Looks like you may also be able to "hold" or "lock" a version in apt-get or dpkg. Check these two references:

[http://ubuntuforums.org/showthread.php?t=855813](http://ubuntuforums.org/showthread.php?t=855813)
[http://www.debian-administration.org/articles/67](http://www.debian-administration.org/articles/67)

Cheers,
Dill

---

### Post by mprince on 2009-05-11
You can 'lock' a version of an application using Synaptics Package manager.

---

