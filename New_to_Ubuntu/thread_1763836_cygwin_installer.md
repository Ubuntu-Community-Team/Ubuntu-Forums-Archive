---
title: "cygwin installer"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by goPlayYourGuitar on 2011-05-20
I just downloaded cygwin and was under the impression I could use it just as I would use the terminal in Ubuntu.  By this I mean that the same commands in Ubuntu would work in cygwin.  For instance, what is the equivalent of "apt-get install" and can I install the same programs with cygwin as I could with Ubuntu?  I feel I may be very off track with this.  Thanks in advance as usual.

---

### Post by beew on 2011-05-20
> **goPlayYourGuitar said:**
> I just downloaded cygwin and was under the impression I could use it just as I would use the terminal in Ubuntu.  By this I mean that the same commands in Ubuntu would work in cygwin.  For instance, what is the equivalent of "apt-get install" and can I install the same programs with cygwin as I could with Ubuntu?  I feel I may be very off track with this.  Thanks in advance as usual.

"apt-get" only works with debian distros and there are similar commands (e.g yum for Fedora) for other distros. All these require some kind of repository systems. Cygwin is not a Linux distro and it doesn't have repository, to install program you need to install from tar balls. Moreover, if you read the cgywin page it is not a way to run Linux programs in Windows, some will work but most wont. 

I tried to install cygwin a while back, it never worked. Somehow some dependencies were always missing.

---

