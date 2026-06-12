---
title: "what does rpm based distro mean?"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by stuart.reinke on 2009-06-07
I want to install a second linux os just to play around with, and have chosen PcLinuxOs. Their home page describes it as a RPM based distro. What does that mean? How is it different than Ubuntu being Debain based (if at all)? 

This seems to be a question born of ingorance. The more I learn about Linux the more I find that I don't know or understand. 

Thanks for any advice or explanation you can give.

Stu

---

### Post by Mornedhel on 2009-06-07
RPM is a different package format, like .deb packages. Thus the two largest distribution families are said to be Debian based (Debian, Ubuntu, derivatives) or RPM based (Mandriva, Red Had/Fedora, derivatives).

With APT, Debian-style packaging introduced a lot of cool features to the world of package-based installation : automatic dependency checking, etc. Nowadays RPM is just as usable since the advent of urpmi and other tools. There is basically no difference for the end-user.

---

### Post by unutbu on 2009-06-07
Ubuntu and Debian uses DPKG for package management. Its packages come in .deb format.

RedHat, and PCLinuxOS use RPM for package management. Its packages come in .rpm format.

Different commands and repositories are used for the distribution of packages.

There is a program called alien which can convert from rpm to deb format and vice versa,
so there is some interoperability, but usually it is recommended that you stick with rpms if you are on an RPM-based distro, (and similarly for debs if you are on an DPKG-based distro.)

---

### Post by ibutho on 2009-06-07
RPM is similar to DPKG on Debian based distros i.e.the basic packaging system. RPM is used by RedHat/Fedora, SUSE/openSUSE, Mandriva, PCLinuxOS and other distros. APT, YUM etc are just frontends to these packaging systems, but they also add features to overcome some limitations. You can also use APT on RPM based distros (.e.g PCLinuxOS), but its no longer very common.

---

### Post by stuart.reinke on 2009-06-07
Thanks to all for clarifying the differences for me. It would seem that many Linux distros are like brothers and sisters. The same, but different. Sometimes compatible, sometimes not. 

The Ubuntu community is the greatest! I'm glad to be a part of it.

---

### Post by kwacka on 2009-06-07
One note, although Debian/Ubuntu/etc uses DPKG package management and PCLinuxOS uses .rpm (Redhat Package Management), PCLinuxOS uses APT's Synaptic graphical interface to install rpms.

You can also install .rpm packages on a .deb system using the 'alien' application.

---

