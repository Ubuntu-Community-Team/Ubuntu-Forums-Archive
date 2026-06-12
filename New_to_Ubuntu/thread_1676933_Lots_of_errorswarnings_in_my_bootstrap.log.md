---
title: "Lots of errors/warnings in my bootstrap.log"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by ErHKfaDvqUf2 on 2011-01-27
First, I would like to say hello, and thank you, to everyone who contributes to this forum. I have been using Ubuntu 10.10 for about a month now and this forum has proved invaluable (considering that this is my first time using any Linux distro).

My question involves my bootstrap.log (whatever that is). 

My system seems to be working great: it's fast, stable, and seems secure, but when I look at my bootstrap.log it is FULL of many types of errors that I don't understand. 

For example, a few lines:

```
warning, in file '/var/lib/dpkg/status' near line 3 package 'dpkg':
 missing description
warning, in file '/var/lib/dpkg/status' near line 3 package 'dpkg':
 missing maintainer
Selecting previously deselected package base-files.
dpkg: regarding .../base-files_5.0.0ubuntu23_i386.deb containing base-files, pre-dependency problem:
 base-files pre-depends on awk
  awk is not installed.
dpkg: warning: ignoring pre-dependency problem!
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_5.0.0ubuntu23_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.22_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you requested:
 base-passwd depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.22) ...
dpkg: base-files: dependency problems, but configuring anyway as you requested:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.

```

This is just the beginning of a long list of warnings in the log. I was wondering if this is normal? I don't think I've done much to invoke all these warnings, but who knows? I am, after all, just a beginner. 

PS: Thanks again and again, and I hope to be an active, helpful member of this community.

---

### Post by Clever_Username on 2011-01-28
I wouldn't worry too much about the errors.
[Here]("http://ubuntuforums.org/showthread.php?t=1625789") is a thread you might find helpful

---

### Post by ErHKfaDvqUf2 on 2011-01-28
Thanks for the quick reply. The link you posted was informative, but my bootstrap.log is still full of all kinds of cryptic errors, even after running: 

```
--clear-avail
```

Still wondering about these warnings. I reinstalled U10.10 on a different machine and get similar messages, even on a clean install. So I won't worry about them... although, I still want to know WHY I shouldn't worry. What exactly are they?

---

### Post by jramshu on 2011-05-11
I get the same warnings in mine too. Anyone know the cause. 

It doesn't seem to affect anything as far as I can tell. I am curious to what the problem is though.

EDIT: Interesting thing, all the packages it says aren't installed are. Odd.

---

### Post by jramshu on 2011-05-11
I'm starting to think these may be incorrect warnings or something. The bootstrap.log says 
```
warning, in file '/var/lib/dpkg/status' near line 3 package 'dpkg':
 missing maintainer
```Says the same about the one near line 48.

I see by this below that the maintainer is there.
```
Package: dpkg
Essential: yes
Status: install ok installed
Priority: required
Section: admin
Installed-Size: 6008
Origin: debian
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: debbugs://bugs.debian.org
Architecture: i386
Version: 1.15.8.4ubuntu3.1
Pre-Depends: libbz2-1.0, libc6 (>= 2.11), libselinux1 (>= 1.32), zlib1g (>= 1:1.1.4), coreutils (>= 5.93-1), xz-utils
Suggests: apt
Breaks: apt (<< 0.7.7), aptitude (<< 0.4.7-1), dpkg-dev (<< 1.14.16), emacs21 (<< 21.4a+1-5.7), emacs21-nox (<< 21.4a+1-5.7), emacs22 (<= 22.2-0ubuntu2), emacs22-gtk (<= 22.2-0ubuntu2), emacs22-nox (<= 22.2-0ubuntu2), jed (<< 1:0.99.18+dfsg.1-13), jed-extra (<= 2.5.3-2), konqueror (<= 4:4.2.96-1), libdpkg-perl (<< 1.15.8), pinfo (<< 0.6.9-3.1), tkinfo (<< 2.8-3.1), xemacs21-support (<< 21.4.22-2), xjed (<< 1:0.99.18+dfsg.1-13)
Conffiles:
 /etc/dpkg/dpkg.cfg f4413ffb515f8f753624ae3bb365b81b
 /etc/alternatives/README 69c4ba7f08363e998e0f2e244a04f881
 /etc/cron.daily/dpkg b6b8dc21210ea50db7cc4636f521758f
 /etc/logrotate.d/dpkg 782ea5ae536f67ff51dc8c3e2eeb4cf9
Description: Debian package management system
 This package provides the low-level infrastructure for handling the
 installation and removal of Debian software packages.
 .
 For Debian package development tools, install dpkg-dev.
Homepage: http://wiki.debian.org/Teams/Dpkg
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>
```Any thoughts on this? Should the maintainer be listed on lines closer to where the log says? Should I even worry about it?

---

### Post by ClientAlive on 2011-05-11
> **jramshu said:**
> I'm starting to think these may be incorrect warnings or something. The bootstrap.log says 
```
warning, in file '/var/lib/dpkg/status' near line 3 package 'dpkg':
 missing maintainer
```Says the same about the one near line 48.

I see by this below that the maintainer is there.
```
Package: dpkg
Essential: yes
Status: install ok installed
Priority: required
Section: admin
Installed-Size: 6008
Origin: debian
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: debbugs://bugs.debian.org
Architecture: i386
Version: 1.15.8.4ubuntu3.1
Pre-Depends: libbz2-1.0, libc6 (>= 2.11), libselinux1 (>= 1.32), zlib1g (>= 1:1.1.4), coreutils (>= 5.93-1), xz-utils
Suggests: apt
Breaks: apt (<< 0.7.7), aptitude (<< 0.4.7-1), dpkg-dev (<< 1.14.16), emacs21 (<< 21.4a+1-5.7), emacs21-nox (<< 21.4a+1-5.7), emacs22 (<= 22.2-0ubuntu2), emacs22-gtk (<= 22.2-0ubuntu2), emacs22-nox (<= 22.2-0ubuntu2), jed (<< 1:0.99.18+dfsg.1-13), jed-extra (<= 2.5.3-2), konqueror (<= 4:4.2.96-1), libdpkg-perl (<< 1.15.8), pinfo (<< 0.6.9-3.1), tkinfo (<< 2.8-3.1), xemacs21-support (<< 21.4.22-2), xjed (<< 1:0.99.18+dfsg.1-13)
Conffiles:
 /etc/dpkg/dpkg.cfg f4413ffb515f8f753624ae3bb365b81b
 /etc/alternatives/README 69c4ba7f08363e998e0f2e244a04f881
 /etc/cron.daily/dpkg b6b8dc21210ea50db7cc4636f521758f
 /etc/logrotate.d/dpkg 782ea5ae536f67ff51dc8c3e2eeb4cf9
Description: Debian package management system
 This package provides the low-level infrastructure for handling the
 installation and removal of Debian software packages.
 .
 For Debian package development tools, install dpkg-dev.
Homepage: http://wiki.debian.org/Teams/Dpkg
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>
```Any thoughts on this? Should the maintainer be listed on lines closer to where the log says? Should I even worry about it?


So, just in case you are curious - here are the locations of the dpkg files and directories in Ubuntu 10.04 (I'm sure they're in the same place on other releases of Ubuntu also thoug.

```
whereis dpkg
dpkg: /usr/bin/dpkg /etc/dpkg /usr/lib/dpkg /usr/share/dpkg /usr/share/man/man1/dpkg.1.gz
```

The "whereis dpkg" is what I entered into the command line and the rest is the response I got. That response shows 5 dpkg named items on the system in 5 dirrerent locations. One of those five is a compressed file.



Just for the heck of it I did a little poking around in these locations to see what some of the names looked like. Here's some of what I found:

```

# cd /etc/dpkg
root@computer:/etc/dpkg# ls
**dpkg.cfg  dpkg.cfg.d  origins**

```

A couple configuration files?



```

root@computer:/usr/bin# file dpkg
dpkg: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```

dpkg is among a very long list of things in /usr/bin. The "file" command shows that at this location it's an executable file.



Lastly - for me tonight anyway:

```

# cd /usr/lib/dpkg
root@computer:/usr/lib/dpkg# ls
methods  mksplit

```

Don't know what those refer too but interesting to look at.



```

root@computer:/usr/lib/dpkg# file mksplit
mksplit: a /usr/bin/perl -- script text executable
root@computer:/usr/lib/dpkg# file methods
methods: directory

```

"file" command shows one's a script text and is executable the other is a directory.



Ok ok, one more . . .  :D

```

root@computer:/usr/lib/dpkg# cd methods
root@computer:/usr/lib/dpkg/methods# ls
apt
root@computer:/usr/lib/dpkg/methods# file apt
apt: directory
root@computer:/usr/lib/dpkg/methods# cd apt
root@computer:/usr/lib/dpkg/methods/apt# ls
desc.apt  install  names  setup  update
root@computer:/usr/lib/dpkg/methods/apt# file install
install: Bourne-Again shell script text executable

```

See? one of those has something to do with bash (the command line in Linux). Pretty cool hun?

---

