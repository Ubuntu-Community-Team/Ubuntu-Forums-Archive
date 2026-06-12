---
title: "PPP on Feisty - Hardware Modem on COM5"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by rasquire on 2007-10-12
For the past year and a half or more, I've been using 5.04 (hoary).  Eventually, it became difficult to get updates through apt-get; even the archives wouldn't work.  So, I order CDs of feisty, backed up my hard drive, and did a fresh install.

Well, now I can't get online for the life of me.  After almost two years with Ubuntu as my default OS, I'm now back to Win98!

I've tried this...

  cd /dev
  mknod ttyS4 c 4 68
  ln -s ttyS4 modem

... with no success.  Neither the Network Manager applet nor command-line ppp apps (like pon) work with my old scripts (which *do* point to /dev/modem).

Has anyone out there managed to get a hardware modem on COM5 working with feisty?

Thanks in advance,
rAS

---

