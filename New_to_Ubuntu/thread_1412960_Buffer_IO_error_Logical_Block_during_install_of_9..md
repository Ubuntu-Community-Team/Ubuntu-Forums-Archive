---
title: "Buffer I/O error Logical Block during install of 9.10"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by RedOctober on 2010-02-21
I've beein installing Ubuntu on a lot of computers lately, using a CD I made of 9.10, and I've found that occasionally on some computers, while the USB CD/DVD is being read, I get a list of the subject type errors.  On other computer installs, these errors do not occur.  I'm always using the same CD and the same USB CD/DVD reader.

These seem like they should be "bad", but, most of the time the OS loads and works correctly anyway.  But I trying to load and old crappy eMachine (just for laffs) and there is a long list of these errors and the OS is corrupted (it won't load again on reboot, and if it does load, I can run the updater, but then, it won't reboot after being updated).

Is my CD corrupted or is it the HD in the target machine that is corrupted?  Or, what is most likely the problem?

---

### Post by sandyd on 2010-02-21
> **RedOctober said:**
> I've beein installing Ubuntu on a lot of computers lately, using a CD I made of 9.10, and I've found that occasionally on some computers, while the USB CD/DVD is being read, I get a list of the subject type errors.  On other computer installs, these errors do not occur.  I'm always using the same CD and the same USB CD/DVD reader.

These seem like they should be "bad", but, most of the time the OS loads and works correctly anyway.  But I trying to load and old crappy eMachine (just for laffs) and there is a long list of these errors and the OS is corrupted (it won't load again on reboot, and if it does load, I can run the updater, but then, it won't reboot after being updated).

Is my CD corrupted or is it the HD in the target machine that is corrupted?  Or, what is most likely the problem?

HD in the machine likely.
If the CD works on multiple computers, it should be the HD.
however, I would check the MD5 sum of the ISO you downloaded and select the option "check disc for errors" at the livecd bootup.

---

### Post by RedOctober on 2010-02-21
I suspected the HD in the target machines, so I did a disk check and the HD report shows it clean, without errors.

---

### Post by RedOctober on 2010-02-21
Ok, now, after a successful install, I reboot, and I get a "mount of file system failed" error.  Any ideas?

---

