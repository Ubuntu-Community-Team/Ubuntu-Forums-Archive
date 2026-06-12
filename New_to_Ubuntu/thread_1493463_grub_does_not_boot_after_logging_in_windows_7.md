---
title: "grub does not boot after logging in windows 7"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by rhuea on 2010-05-25
Hello everone, im having trouble with my laptop. I recently put lucid in a new laptop with windows 7. everything is working fine until i logged in in windows 7. after a restart, grub doesn't show up and the machine enters an endless loop of shutting down and re-opening. advice will be very much appreciated. Thank you all.

---

### Post by oldfred on 2010-05-25
Some windows software writes hidden info into the MBR which is supposed to be reserved for booting. Grub2 is slightly larger than the windows boot loader or old grub legacy which then causes conflicts.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

