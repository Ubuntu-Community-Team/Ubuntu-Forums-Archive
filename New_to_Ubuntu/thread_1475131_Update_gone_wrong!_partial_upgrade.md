---
title: "Update gone wrong! partial upgrade"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by tombepa on 2010-05-06
My update manager came up today with a lot of updates, I said ok. My computer shut down before the updates could finish. When I went back in to the update manager it said I needed to do a partial upgrade. I ran sudo dpkg --configure -a to try to fix and I get this:


patrick@patrick-laptop:~$ sudo dpkg --configure -a
Setting up empathy-common (2.30.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing empathy-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on empathy-common (= 2.30.1-0ubuntu1); however:
  Package empathy-common is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-sendto-empathy:
 nautilus-sendto-empathy depends on empathy-common (= 2.30.1-0ubuntu1); however:
  Package empathy-common is not configured yet.
dpkg: error processing nautilus-sendto-empathy (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.98-1ubuntu6) ...
/usr/sbin/grub-probe: error: not a directory.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
Generating grub.cfg ...
/usr/sbin/grub-probe: error: not a directory.
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc; however:
  Package grub-pc is not configured yet.
dpkg: error processing grub2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 empathy-common
 empathy
 nautilus-sendto-empathy
 grub-pc
 grub2
patrick@patrick-laptop:~$ 

What do I do now?

---

### Post by tombepa on 2010-05-06
nevermind, I did not have much on this system so I burned the iso and did a fresh install. All is well.

---

### Post by -humanaut- on 2010-05-07
Just for the record if a "partial upgrade" shows up again Don't upgrade it. They can cause serious issues and potentially break your entire system.

---

### Post by tombepa on 2010-05-07
thanks for the info.

---

### Post by sidneylopsides on 2010-05-08
I just got this exact error. 
I'm pretty new to Ubuntu, and Linux, so I have no idea how to fix this. 
Can anyone help? I'd rather not do a fresh install as I have stuff on here now, and haven't worked out how to make partitions...

edit: fiddled and used purge, all seems fine now!

---

### Post by tombepa on 2010-05-09
how do you purge just in case it happens to me again? if you don't mind me asking.

---

