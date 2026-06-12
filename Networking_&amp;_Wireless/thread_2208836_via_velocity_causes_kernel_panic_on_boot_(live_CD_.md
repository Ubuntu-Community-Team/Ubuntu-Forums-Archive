---
title: "via velocity causes kernel panic on boot (live CD or installed version of 13.10)"
date: 2014-03-02
forum: Networking &amp; Wireless
---

### Post by keithspg on 2014-03-02
This is an old, known bug (since october 2013). I cannot post it as a bug because of the archane reporting process. 

I do want to help, though. 

You know if you have this bug if: A) you have the via-velocity ethernet module loaded and B) it freezes as soon as it tries to get an IP address. The computer freezes as soon as network manager tried to bring the interface up. You can actually install (x,k)ubuntu (or mint), but cannot have the ethernet cord plugged in or this will happen every time. This is the same for 32 bit as well as 64 bit versions of ubuntu and all ubuntu based distros. As soon as you bring up the interface it freezes and the only recourse I have found is a power down. This is fixed in upstream kernels but NONE of the ubuntu/mint variants of 13.10 have this fix, yet. Yes, even after a dist-upgrade, this is not fixed. 

You have to compile the kernel module and replace the buggy one in the module directory. I grabbed the source from linus' own kernel repository (it is attached) and found out how to compile it here:
[http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html)
also from these forums:
[http://ubuntuforums.org/showthread.php?t=1153067](http://ubuntuforums.org/showthread.php?t=1153067)

I have tried this with xubuntu and linux mint (both based on saucy) and this works (mint is still running 3.11.0-12 and (xu,ku,u)buntu are running 3.11.0.17 at the date of this post). If anyone can/wants to report this as a bug so saucy gets fixed, feel free. I cannot figure out how to alert canonical.

Let me know if you find this useful

Keith

---

### Post by keithspg on 2014-03-04
I just tried xubuntu 14.04 and have a different embodiment of the bug but similar result. I have my isos on a PXE server. I can boot the live CD on one computer that uses a Realtek ethernet card, but not on the one that uses the via-velocity card. When this one fails, it shuts down the computer (power off). With 13.10, it just printed a kernel panic with the boot messages when it tried to bring up the interface. I did not check to see which kernel version the 14.04 beta is using, but it is definitely broken. Once again. I have no idea who to report this to, though I can point to the solution.

The solution is in this thread:
[http://www.spinics.net/lists/netdev/msg251287.html](http://www.spinics.net/lists/netdev/msg251287.html)

The upstream kernel repository appears to be patched (linus' current git repository) but the 14.04 kernel does not appear to be or maybe it is another regression bug.

Am I the only one trying to run this on a machine with a via-velocity ethernet card?

Keith

---

### Post by keithspg on 2014-03-16
If anyone knows how, report this to the kernel maintainer group to fix this bug by using the current driver source to compile the kernel driver.

---

