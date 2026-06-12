---
title: "Kernel Panic - not syncing:-VFS:- Unable to mount root fs on unknown block"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by jfreak_ on 2010-09-01
Me having a desktop with windows 7 ultimate installed.
I installed ubuntu 9.10 inside my windows.
After that i boot it no problem  found .Till here all went fine
Then i upgraded to 10.04lts after that when i try to i found a message grub rescue:>
I somehow managed.I repair the startup using widows 7 dvd .
After i repaired i login to ubuntu 10.4. then i updated my nvidia graphics card after that i restarted .
Then i got this message:[ 0.667074 ]Kernel Panic - not syncing:-VFS:- Unable to mount root fs on unknown block


  sudo mount /dev/sda2/mnt
it says it cant mount it:confused:

---

### Post by jtarin on 2010-09-01
> **jfreak_ said:**
> Me having a desktop with windows 7 ultimate installed.
I installed ubuntu 9.10 inside my windows.
After that i boot it no problem  found .Till here all went fine
Then i upgraded to 10.04lts after that when i try to i found a message grub rescue:>
I somehow managed.I repair the startup using widows 7 dvd .
After i repaired i login to ubuntu 10.4. then i updated my nvidia graphics card after that i restarted .
Then i got this message:[ 0.667074 ]Kernel Panic - not syncing:-VFS:- Unable to mount root fs on unknown block


  sudo mount /dev/sda2/mnt
it says it cant mount it:confused:Upgrading to 10.04 means you upgraded to GRUB2 from GrubLegacy, which has different config files. Did you install GRUB2 during the 10.04 install and where did you install too?

[Here's more info on WUBI]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by jtarin on 2010-09-01
[More info on this BUG in WubI and some workarounds.]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all")
[And more work arounds.]("http://ubuntuforums.org/showthread.php?t=1007816")...You really should dual boot.

---

### Post by bcbc on 2010-09-01
> **jfreak_ said:**
> Me having a desktop with windows 7 ultimate installed.
I installed ubuntu 9.10 inside my windows.
After that i boot it no problem  found .Till here all went fine
Then i upgraded to 10.04lts after that when i try to i found a message grub rescue:>
I somehow managed.I repair the startup using widows 7 dvd .
After i repaired i login to ubuntu 10.4. then i updated my nvidia graphics card after that i restarted .
Then i got this message:[ 0.667074 ]Kernel Panic - not syncing:-VFS:- Unable to mount root fs on unknown block


  sudo mount /dev/sda2/mnt
it says it cant mount it:confused:
Have you tried booting a previous kernel?

---

### Post by jfreak_ on 2010-09-01
thank u. i downloaded latest wuibldr. and replaced with old one.
thank u for helping me out

---

### Post by jtarin on 2010-09-01
Your welcome. You might mark this thread as solved.

---

