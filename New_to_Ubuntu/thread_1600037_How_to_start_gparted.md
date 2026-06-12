---
title: "How to start gparted?"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by hekastos on 2010-10-18
When I start gparted (or from system/administration) this happens:

```

sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

```It seems this bug:
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885)
but I don|t really understand the fix.
apt-cache policy gparted
gives me
```

  Installed: 0.6.2-1ubuntu1
  Candidate: 0.6.2-1ubuntu1
  Version table:
 *** 0.6.2-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ maverick/main i386 Packages
        100 /var/lib/dpkg/status

```Any help would be greatly appreciated!

---

### Post by heyandy889 on 2010-10-18
Hi, hekastos!

From the bug page you posted, it looks like a possible fix might be using the command "gksudo gparted" in place of "sudo gparted". The man pages for both sudo and gksudo give some general enlightenment as to how they differ.

Maybe "gksudo gparted" will work?

---

### Post by blueridgedog on 2010-10-18
It appears the bug is still unresolved.  Can you tell me what you are trying to do and perhaps I can assist you with other tools.

---

### Post by hekastos on 2010-10-18
@heyandy889
gksu gives me the same error (but a much nicer password entry field ;) )

this guy seth writes in comment 12-13 of the bug report something interesting, but I'm not quite sure if I understand it right ;)

@blueridgedog
somehow I killed my swap partition, I wanted to reinstall it, but gparted didn't work, so I tried the live ubuntu CD but with the same result. then I tried the live gparted cd and that worked and so I have my swap back, but since I like to be able to partition stuff (i.e. new hdd in or extern) etc. pp. I thought, after a whole day battling ubuntu I can try to tackle this problem too, and perhaps add this solution, to my battles of the day...

---

### Post by blueridgedog on 2010-10-18
Do you still get the error now that you have repaired the partition?  I don't see a work around for this unless you run from the gparted cd.  I suspect a patch will be forthcoming, but the bug is a bit to new to have the working patch rolled out just yet.

---

### Post by hekastos on 2010-10-18
Since I repaired the partition, the system works again, but no matter what, gparted live cd is my only way to get a gparted running. The Error stays.
I thought I could fix it, because of comment #40 in the bug report, but I'm to stupid or the bug is a bit bigger then it seemed...
Can I do anything with parted what I could do with gparted?

---

### Post by blueridgedog on 2010-10-18
There are terminal commands for making, deleting and formating partitions that vastly predate gparted.  This includes parted, fdisk and mkfs.  You can read about them with the man command or use google.  They are the tools you use when you manage systems without a graphical window manager or a remote system.  Most system admins will still use fdisk and mkfs over gparted.

---

### Post by hekastos on 2010-10-19
Thx a lot, so I will wait, hope for a fix and entertain me during that with man pages... ;)
Shall I mark this tread as solved (because it actually isn't, I just agree with you its more hassle then a few manpages for command line tools...)?

---

