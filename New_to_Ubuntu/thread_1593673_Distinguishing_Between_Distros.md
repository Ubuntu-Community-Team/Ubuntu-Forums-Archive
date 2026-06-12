---
title: "Distinguishing Between Distros"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by zer010 on 2010-10-11
Just out of curiosity, what is a surefire way to tell what distro a PC is running WITHOUT rebooting? I ask, because I'm sure I've seen some PCs used by a retail store running some form of Linux. I just don't know what distro they are using and I'm sure they would be upset if I sneaked behind the counter and reset it. :lolflag: 
Usually, the person using the PC probably wouldn't even know that it's Linux, just some 'proprietary system'.:P

---

### Post by qyot27 on 2010-10-11
uname -a

[http://en.wikipedia.org/wiki/Uname](http://en.wikipedia.org/wiki/Uname)

---

### Post by lykwydchykyn on 2010-10-11
Traditionally the /etc/issue file contains the name of the distro and version, but this is only convention AFAIK and certainly not required.

---

### Post by zer010 on 2010-10-12
Thanks! Y'all have satisfied my curiosity. *thumbs up*

---

### Post by srs5694 on 2010-10-12
The "uname -a" command does *not* reveal the distribution, at least not in a sure-fire way. It displays information on the CPU, kernel, and hostname. *If* the computer is running the distribution's stock kernel, and *if* the distribution includes a code for its name in the kernel version number, you'll get that code, but you'll still need to interpret it. If the system runs a locally compiled kernel or if the distribution's kernel doesn't include such a code, you'll see nothing to identify the distribution. For instance, here's what I get on one of my systems:

```

$ uname -a
Linux nessus 2.6.35.5 #3 SMP PREEMPT Sun Sep 26 23:32:11 EDT 2010 x86_64 AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ AuthenticAMD GNU/Linux
```

Ubuntu's /etc/issue file does include the distribution name, but that's not true of every distribution's /etc/issue file. This file's purpose is to hold information that's displayed when a user logs in using a local text-mode console, so administrators may change it to identify their site, an acceptable use policy, or whatnot rather than the distribution used.

A more generally applicable method is to look for a file called /etc/*-release, where "*" can be anything but is generally either "lsb" or the distribution name. This file contains the name and version of the distribution. For instance:

```
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

```

On another system:

```

$ cat /etc/gentoo-release 
Gentoo Base System release 1.12.13

```

More generally, "cat /etc/*-release" will do the job if you don't already know the distribution name.

---

### Post by zer010 on 2010-10-13
Cool! Thanks!

---

