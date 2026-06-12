---
title: "cannot install acroread"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by aam-aadmi on 2009-09-04
Hi All,

I am using Ubuntu 9.04 and am trying to install "acroread". I added the medibuntu repository and then tried to install acroread by

[HTML]sudo apt-get install acroread[/HTML]

and this is the message I get:

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
[/HTML]

The last few lines of my /etc/apt/sources.list file is:

[HTML]## Medibuntu - Ubuntu 8.10 "jaunty jackalope"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free
[/HTML]

What is the mistake I am making?

Aam-aadmi

---

### Post by defacto on 2009-09-04
Mediabuntu offers only x64 acroread. Fire up Add/Remove and search for acroread - upon enabling partner repositories, you will be able to install it.
Indeed, why you're using 8.10 Mediabuntu repository for 9.04 ( Jaunty ) ?

---

### Post by aam-aadmi on 2009-09-04
Thanks; I could install Adobe Reader 9 through the "add/remove applications" option.  

By the way, the repository for Medibuntu is correct:

[HTML]deb http://packages.medibuntu.org/ jaunty free non-free[/HTML]

The commented line had a typo in that it wrote Ubuntu 8.10 instead of 9.04.

Aam-aadmi

---

### Post by defacto on 2009-09-04
> **aam-aadmi said:**
> Thanks; I could install Adobe Reader 9 through the "add/remove applications" option.  

By the way, the repository for Medibuntu is correct:

[html]deb http://packages.medibuntu.org/ jaunty free non-free[/html]The commented line had a typo in that it wrote Ubuntu 8.10 instead of 9.04.

Aam-aadmi

Ah, yeah .. comment line popped out a little bit faster than repository entries and I didn't looked any further.

---

