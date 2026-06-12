---
title: "Reading logs."
date: 2011-01-27
forum: New to Ubuntu
---

### Post by weedeater64 on 2011-01-27
I wasn't sure where to put this, but decided on here because of the description of the  package ksystemlog, see below..

More a survey than question. I'm wondering what people are using for viewing/analyzing logs.

Been a while since I've spent any time looking at logs, but I want to spend some time perusing now.

cat |less 

will work

cat |grep 

works better, if you know what you are looking for.

Browsers are Ok, but I think I want to try one of these filtering/analyzing utilities out.

So what are you guys using? The following description sound good. I don't think I want to try many and pick, but rather take some polls and maybe try two, three tops..

thanks

```
jeff@optiplex:~$ acsh ksystemlog
Package: ksystemlog
Priority: optional
Section: admin
Installed-Size: 580
Maintainer: Debian KDE Extras Team <pkg-kde-extras@lists.alioth.debian.org>
Architecture: i386
Version: 0.3.2-1
Depends: kdelibs4c2a (>= 4:3.5.4-1), libc6 (>= 2.3.6-6), libgcc1 (>= 1:4.1.0), libqt3-mt (>= 3:3.3.6), libstdc++6 (>= 4.1.0)
Filename: pool/main/k/ksystemlog/ksystemlog_0.3.2-1_i386.deb
Size: 209046
MD5sum: 85fe124d8e1b273ed1e0772634d5ebe5
SHA1: 67a5c3dad7bdb36331086b4c502c8b7162b95458
SHA256: 4a27d87fa6f8df5c27619a42b899c6b21811179218501fdbf61350530c255578
Description: system log viewer tool for KDE
 ksystemlog is a system log viewer tool for KDE.
 .
 This program is developed for being used by beginner users, which don't know
 how to find information about their Linux system, and how the log files are in
 their computer. But it is also designed for advanced users, who want to
 quickly see problems occuring on their server.
 .
  Homepage: http://ksystemlog.forum-software.org
Tag: implemented-in::c++, interface::x11, role::program, security::log-analyzer, suite::kde, uitoolkit::qt, works-with::logfile, x11::application
```

---

### Post by 1clue on 2011-01-27
You don't need cat with either of those options.  You could type 'less /var/log/messages' and it would work the same.  'grep -i dhcp /var/log/messages' would find all lines containing 'dhcp' in any capitalization scheme.

You covered most of my use cases with less and grep.  I also sometimes use vim, or if I need to get a real-time log I use tail -F ....

---

