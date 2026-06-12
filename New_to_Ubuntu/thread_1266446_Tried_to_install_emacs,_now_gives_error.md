---
title: "Tried to install emacs, now gives error"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by pedro3005 on 2009-09-14
I tried to install emacs with apt-get, it gave an error. Now trying to purge it fails:
```

pedro@pedro:~$ sudo apt-get purge emacs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emacs is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up emacs22-gtk (22.2-0ubuntu2) ...
update-alternatives: unable to make /usr/share/man/ru/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.ru.1.gz: No such file or directory
dpkg: error processing emacs22-gtk (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emacs22-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What can I do?

---

### Post by lukjad on 2009-09-15
> **pedro3005 said:**
> I tried to install emacs with apt-get, it gave an error. Now trying to purge it fails:
```

pedro@pedro:~$ sudo apt-get purge emacs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emacs is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up emacs22-gtk (22.2-0ubuntu2) ...
update-alternatives: unable to make /usr/share/man/ru/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.ru.1.gz: No such file or directory
dpkg: error processing emacs22-gtk (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emacs22-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What can I do?
Try this: ```
sudo apt-get -f install emacs
```

---

### Post by pedro3005 on 2009-09-15
Thanks, but didn't work :(
```

pedro@pedro:~$ sudo apt-get -f install emacs
[sudo] password for pedro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  emacs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 6362B of archives.
After this operation, 36.9kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com jaunty/main emacs 22.2-0ubuntu2 [6362B]
Fetched 6362B in 1s (5798B/s)                       
Selecting previously deselected package emacs.
(Reading database ... 163303 files and directories currently installed.)
Unpacking emacs (from .../emacs_22.2-0ubuntu2_all.deb) ...
Setting up emacs22-gtk (22.2-0ubuntu2) ...
update-alternatives: unable to make /usr/share/man/ru/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.ru.1.gz: No such file or directory
dpkg: error processing emacs22-gtk (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs22-gtk | emacs22 | emacs22-nox; however:
  Package emacs22-gtk is not configured yet.
  Package emacs22 is not installed.
  Package emacs22-gtk which provides emacs22 is not configured yet.
  Package emacs22-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 emacs22-gtk
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by jpkotta on 2009-09-16
emacs is not a real package.  You want emacs22 or better yet emacs-snapshot.  It is used by the package manager to indicate than *an* emacs has been installed.

```

$ aptitude show emacs
Package: emacs
New: yes
State: installed
Automatically installed: no
Version: 22.2-0ubuntu2
Priority: optional
Section: editors
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 36.9k
Depends: emacs22-gtk | emacs22 | emacs22-nox
Provides: editor, emacsen, info-browser, mail-reader, news-reader
Description: The GNU Emacs editor **(metapackage)**
 GNU Emacs is the extensible self-documenting text editor. This is a metapackage which will always depend on the latest
 Emacs release.

```

---

### Post by pedro3005 on 2009-09-16
It gave me this error:
```

pedro@pedro:~$ sudo apt-get install emacs-snapshot
[sudo] password for pedro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  emacs-snapshot-bin-common emacs-snapshot-common
Suggested packages:
  emacs-snapshot-el
The following NEW packages will be installed:
  emacs-snapshot emacs-snapshot-bin-common emacs-snapshot-common
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 18.2MB of archives.
After this operation, 74.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com jaunty/universe emacs-snapshot-common 1:20090320-1ubuntu1 [16.2MB]
Get:2 http://archive.ubuntu.com jaunty/universe emacs-snapshot-bin-common 1:20090320-1ubuntu1 [134kB]
Get:3 http://archive.ubuntu.com jaunty/universe emacs-snapshot 1:20090320-1ubuntu1 [1808kB]
Fetched 18.2MB in 3min 6s (97.3kB/s)                                           
Selecting previously deselected package emacs-snapshot-common.
(Reading database ... 163307 files and directories currently installed.)
Unpacking emacs-snapshot-common (from .../emacs-snapshot-common_1%3a20090320-1ubuntu1_all.deb) ...
Selecting previously deselected package emacs-snapshot-bin-common.
Unpacking emacs-snapshot-bin-common (from .../emacs-snapshot-bin-common_1%3a20090320-1ubuntu1_i386.deb) ...
Selecting previously deselected package emacs-snapshot.
Unpacking emacs-snapshot (from .../emacs-snapshot_1%3a20090320-1ubuntu1_i386.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up emacs22-gtk (22.2-0ubuntu2) ...
update-alternatives: unable to make /usr/share/man/ru/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.ru.1.gz: No such file or directory
dpkg: error processing emacs22-gtk (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs22-gtk | emacs22 | emacs22-nox; however:
  Package emacs22-gtk is not configured yet.
  Package emacs22 is not installed.
  Package emacs22-gtk which provides emacs22 is not configured yet.
  Package emacs22-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
Setting up emacs-snapshot-common (1:20090320-1ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Setting up emacs-snapshot-bin-common (1:20090320-1ubuntu1) ...

Setting up emacs-snapshot (1:20090320-1ubuntu1) ...
update-alternatives: unable to make /usr/share/man/ru/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.ru.1.gz: No such file or directory
dpkg: error processing emacs-snapshot (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for menu ...
Errors were encountered while processing:
 emacs22-gtk
 emacs
 emacs-snapshot
E: Sub-process /usr/bin/dpkg returned an error code (1)
pedro@pedro:~$ sudo apt-get install emacs-snapshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emacs-snapshot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up emacs-snapshot (1:20090320-1ubuntu1) ...
update-alternatives: unable to make /usr/share/man/ru/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.ru.1.gz: No such file or directory
dpkg: error processing emacs-snapshot (--configure):
 subprocess post-installation script returned error exit status 2
Setting up emacs22-gtk (22.2-0ubuntu2) ...
update-alternatives: unable to make /usr/share/man/ru/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.ru.1.gz: No such file or directory
dpkg: error processing emacs22-gtk (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs22-gtk | emacs22 | emacs22-nox; however:
  Package emacs22-gtk is not configured yet.
  Package emacs22 is not installed.
  Package emacs22-gtk which provides emacs22 is not configured yet.
  Package emacs22-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 emacs-snapshot
 emacs22-gtk
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by unutbu on 2009-09-16
I notice this error:
```

update-alternatives: unable to make /usr/share/man/ru/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.ru.1.gz: No such file or directory

```

Perhaps you tried to purge languages from your computer that you do not use?
For some reason, emacs-snapshot seems to be packaged in a way that assumes the directory /usr/share/man/ru/man1/ exists.
I think perhaps it would be easiest to accomodate emacs-snapshot and just create the directory:
```

sudo mkdir -p /usr/share/man/ru/man1/
```

Then try installing emacs-snapshot again.

---

### Post by pedro3005 on 2009-09-16
Yeah, I did purge languages I don't use (all but english). I tried that but it complains about yet a different language:
```

pedro@pedro:~$ sudo mkdir -p /usr/share/man/ru/man1/
[sudo] password for pedro: 
pedro@pedro:~$ sudo apt-get install emacs-snapshot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emacs-snapshot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up emacs-snapshot (1:20090320-1ubuntu1) ...
update-alternatives: unable to make /usr/share/man/pl.ISO8859-2/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.pl.ISO8859-2.1.gz: No such file or directory
dpkg: error processing emacs-snapshot (--configure):
 subprocess post-installation script returned error exit status 2
Setting up emacs22-gtk (22.2-0ubuntu2) ...
update-alternatives: unable to make /usr/share/man/pl.ISO8859-2/man1/editor.1.gz.dpkg-tmp a symlink to /etc/alternatives/editor.pl.ISO8859-2.1.gz: No such file or directory
dpkg: error processing emacs22-gtk (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs22-gtk | emacs22 | emacs22-nox; however:
  Package emacs22-gtk is not configured yet.
  Package emacs22 is not installed.
  Package emacs22-gtk which provides emacs22 is not configured yet.
  Package emacs22-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 emacs-snapshot
 emacs22-gtk
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How may I get them all back?

---

### Post by unutbu on 2009-09-16
Umm... I'm not really sure. I think what you are experiencing happens only when you manually delete files that were installed by a package. The whole package system comes tumbling down because scripts assume certain files and directories to exist, and suddenly they do not. 

Manually recreating the directories that apt-get is complaining about might be the easiest way to fix the problem, and would be ample reminder to never delete files owned by packages again. 

Sorry I don't have a better solution -- one may exist, but I don't know it.

Edit: There is a package called "localepurge" which is supposed to allow you to remove locales (languages) you do not need. I have never tried it myself, however, because 
the description of the package scared me away:

```
 Please note, that this tool is a hack which is *not* integrated with
 Debian's package management system and therefore is not for the faint
 of heart. This program interferes with the Debian package management
 and does provoke strange, but usually harmless, behaviour of programs
 related with apt/dpkg like dpkg-repack, debsums, reportbug, etc.
 Responsibility for its usage and possible breakage of your system
 therefore lies in the sysadmin's (your) hands.
```

Given your current situation, however, you might want to try installing it and seeing if that clears away your problem. See Tip #3: [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

---

### Post by pedro3005 on 2009-09-16
Well I do have localepurge and use it. Never thought it'd cause problems. So my solution is to manually re-create them all?

---

### Post by unutbu on 2009-09-16
Yes, as annoying as it sounds, I know of no easier way than to just manually re-create the files and directories. 

When you see```


unable to make /usr/share/man/pl.ISO8859-2/man1/editor.1.gz.dpkg-tmp
```

try 
```

sudo mkdir -p /usr/share/man/pl.ISO8859-2/man1/
```

The "-p" flag tells mkdir to create all necessary subdirs.

If it complains of a file not found, you can create an empty file with```


sudo touch /path/to/file
```

---

### Post by pedro3005 on 2009-09-16
Well then I bet it is possible to create a script to automate that. How would it be?

---

