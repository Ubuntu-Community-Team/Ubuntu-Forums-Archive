---
title: "Git 1.7.0, now what?"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by markerline on 2010-02-24
I downloaded Git 1.7.0 to replace 1.6.3.3 so that I could build Google Chrome OS from source code.  I need help installing Git.  I tried using sudo make after ./configure and sudo make install but I got errors.  I'm new to bash.

---

### Post by bmbaker on 2011-02-21
> **markerline said:**
> I downloaded Git 1.7.0 to replace 1.6.3.3 so that I could build Google Chrome OS from source code.  I need help installing Git.  I tried using sudo make after ./configure and sudo make install but I got errors.  I'm new to bash.

I am just looking into this myself, and was wondering if you got it figured out ?
thanks
BB

---

### Post by gmargo on 2011-02-21
You'd be better off using this ppa, which has the latest git stable release:

[https://launchpad.net/~git-core/+archive/ppa]("https://launchpad.net/%7Egit-core/+archive/ppa")

---

### Post by KIAaze on 2011-02-21
> **markerline said:**
> I downloaded Git 1.7.0 to replace 1.6.3.3 so that I could build Google Chrome OS from source code.  I need help installing Git.  I tried using sudo make after ./configure and sudo make install but I got errors.  I'm new to bash.

Only use sudo for "sudo make install".
"./configure" and "make" do normally not require sudo.

However, as gmargo suggested, you would be better off using the PPA.

---

