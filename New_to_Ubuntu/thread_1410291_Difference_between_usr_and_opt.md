---
title: "Difference between usr and opt"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by A_M_S on 2010-02-18
Can anyone explain  the difference between the following directories in the Linux filesystem:

/opt
/usr/local
/usr/share

Why there are so many places in Linux for the installed binaries ?

Tnx.

---

### Post by MinimalBin on 2010-02-18
/opt is generally used for software which can not be *installed* - as an example, Eclipse .. there's no way you could install it ( as there's no installer inside ) unless someone makes a special build for it. All you do is extract the package, move to a folder where it can be easily accessed and create a symlink or simply add the appropriate /opt sub-directory to the PATH variable.

---

### Post by mcduck on 2010-02-18
/usr is the standard location for all user-level applications and files.

/opt is just a place for custom stuff, things that don't really belong into the system, like programs you download manually and compile from source code, or that you for some other reason want to keep separate from all the normal stuff on your system.

---

### Post by bodhi.zazen on 2010-02-18
> **A_M_S said:**
> Can anyone explain  the difference between the following directories in the Linux filesystem:

/opt
/usr/local
/usr/share

Why there are so many places in Linux for the installed binaries ?

Tnx.

[img]http://geniushackers.com/blog/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg[/img]

There is some variation across distros of course.

In general, additional or optional or non-core software (ie from outside the official repositories) is often installed in either /opt or /usr/local (varies).

the binaries are organized somewhat into system binaries (for sys admin) and "user" or applications. USR - Unix System Resources (not short for user) ;)

---

### Post by A_M_S on 2010-02-18
Thank you guys!:)

---

### Post by Shark_AtK12 on 2010-02-18
Love the pictures. Saving that

---

