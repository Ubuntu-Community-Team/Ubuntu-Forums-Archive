---
title: "[proftpd] lock all users to one directory"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by lofttroy on 2009-04-01
I have an fpt site up and it works fine with a single user.

Here's what I'm trying to do, I just don't know how to setup proftpd.conf

This machine is CLI only so no gproftpd.

Multiple system UIDs, User1, User2, UserN
(All users use their own system password)
All ftp locked to a single ftp directory: /mydrive/ftproot
Incoming directory at /mydrive/ftproot/Incoming is writeonly, nonlisting, nooverwrites
All other subdirectories from ftproot are readonly

On another vaguely related note when I add a <Limit LOGIN> section to my conf file it generates an error no matter where I place it.  Bad ACL definition.  I'd like to stop all the ftp attempts from random domains.  (I don't know anyone in *.tr, *.ch, *.ru)

Any help is gratefully accepted.

Troy

---

