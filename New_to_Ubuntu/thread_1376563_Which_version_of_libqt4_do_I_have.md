---
title: "Which version of libqt4 do I have?"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by tidmarsh on 2010-01-09
Hi--

I'm running 64-bit Jaunty with kernel 2.6.28-17-generic and Gnome 2.26.1 on a Gateway notebook with 2 Gb of RAM and Intel T3400 processor at 2.16GHz. I have also installed Kubuntu desktop.

Here's the short question: Synaptic shows the installed version of libqt4 as "4.5.0-0ubuntu4.3"; is that qt 4.5 or qt 4.3? How do I upgrade to a more recent version?

Here's the context: I'm trying to install [SocNetV]("http://socnetv.sourceforge.net/") to do some social network analysis. Version 0.51 from the repositories crashes when I try to load a large data set, so I'm trying to compile the latest version, 0.8, from source. 

After unpacking the source tarball,  I sudo ./configure. The configuration stops with the message, "checking for Qt library version >= 4.4... no; Qt 4.4 or greater is required."

I've also found a .deb file for version 0.70, but it hangs with the message, "Error: dependency is not satisfiable: libqt4 network (>=4.5.1)."

How do I go about getting the most recent libqt4?

---

### Post by SuperSonic4 on 2010-01-09
I have Qt 4.6-5.

I believe the latest stable version is 4.5

---

### Post by tidmarsh on 2010-01-09
So if I have Qt 4.6, does anyone have ideas for how to get SocNetV to compile?

---

### Post by SuperSonic4 on 2010-01-09
does ```
dpkg -i --force-architecture SocNetV-0.80.deb
``` work?

I'll take a look at the source code in a min.

EDIT: From the INSTALL file it looks like you need qt4-dev-tools:```
sudo apt-get install qt4-dev-tools
```

---

### Post by tidmarsh on 2010-01-09
AHA! Success!

Thanks for the quick help.

---

