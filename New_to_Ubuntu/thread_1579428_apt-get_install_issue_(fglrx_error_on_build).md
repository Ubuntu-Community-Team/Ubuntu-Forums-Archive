---
title: "apt-get install issue (fglrx error on build)"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by excetara2 on 2010-09-21
Whenever I run apt-get install I get these messages which I didn't before. Is there an easy fix?


Setting up fglrx (2:8.771-0ubuntu0sarvatt~lucid) ...
Removing old fglrx-8.771 DKMS files...

------------------------------
Deleting module version: 8.771
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.771 DKMS files...
Building only for 2.6.32-24-generic
Building for architecture x86_64
Building initial module for 2.6.32-24-generic

Error! Bad return status for module build on kernel: 2.6.32-24-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_AU.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sandyd on 2010-09-21
> **excetara2 said:**
> Whenever I run apt-get install I get these messages which I didn't before. Is there an easy fix?


Setting up fglrx (2:8.771-0ubuntu0sarvatt~lucid) ...
Removing old fglrx-8.771 DKMS files...

------------------------------
Deleting module version: 8.771
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.771 DKMS files...
Building only for 2.6.32-24-generic
Building for architecture x86_64
Building initial module for 2.6.32-24-generic

Error! Bad return status for module build on kernel: 2.6.32-24-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_AU.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
run update manager.
theirs a new kernel 2.6.32-25-generic.

---

### Post by excetara2 on 2010-09-23
I had run update manager but I just purged the fglrx and no more issues. I don't use that driver anyway so no issues now. I will go grab the new kernel.

Cheers

---

### Post by sandyd on 2010-09-23
> **excetara2 said:**
> I had run update manager but I just purged the fglrx and no more issues. I don't use that driver anyway so no issues now. I will go grab the new kernel.

Cheers
if you need to actually use it, ive posted the fix in my signature..

---

### Post by messie on 2010-09-24
Hi I had the same issue

however, after purging the fglrx I get nothing but a black screen. Funny as it sounds, I cannot also get the new kernel 2.6.32-25-generic... I have tried this
[http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/](http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/)

but it states that the new kernel is not there. Any ideas?

---

### Post by sandyd on 2010-09-24
> **messie said:**
> Hi I had the same issue

however, after purging the fglrx I get nothing but a black screen. Funny as it sounds, I cannot also get the new kernel 2.6.32-25-generic... I have tried this
[http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/](http://www.cyberciti.biz/faq/howto-upgrading-the-ubuntu-linux-kernel/)

but it states that the new kernel is not there. Any ideas?
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.fglrx

---

### Post by messie on 2010-09-25
Thanks a million pal, I have been searching everywhere for a solution. That did the trick!

---

### Post by pcolamar on 2010-09-25
> **sandyd said:**
> if you need to actually use it, ive posted the fix in my signature..

Thanks for the hint Sandyd,
  I had the same problem, followed you signature link and... BINGO !

Cheers
Palmer

---

### Post by excetara2 on 2010-09-26
Haven't been following this but no I can't use fglrx because doesn't work properly with suspend and hibernate after days of frustration trying to get it working so I just gave up because don't really do graphic intensive work often and the open drivers work great with everything I run.

I don't see the new Kernel in update manager??

Any reason for that?

---

