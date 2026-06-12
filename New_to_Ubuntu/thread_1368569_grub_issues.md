---
title: "grub issues"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by stunningman on 2009-12-30
i have ubuntu 9.04 installed in my system and i am planning to install opensuse 11.2 along side.i want to know the grub setting so that ubuntu 9.04 shows and boots properly from opensuse's grub menu.

my present grub menu shows both ubuntu and windows boot option.
what precautions should be taken.before hand.

:confused:

---

### Post by TetonsGulf on 2009-12-30
It used to be you could install to a new partition and the installer would keep Ubuntu in your GRUB options, but I think that easy answer changed when Ubuntu 9.10 went to GRUB2. 

Good news is I think I read that openSUSE 11.2 still uses GRUB legacy and I know Ubuntu 9.04 did... you shouldn't have a problem with the option staying put, but just in case, these links should help out should you lose your way:

[http://forums.opensuse.org/install-boot-login/425460-installing-11-2-alongside-ubuntu.html](http://forums.opensuse.org/install-boot-login/425460-installing-11-2-alongside-ubuntu.html)

[http://ubuntu.swerdna.org/ububootsuse.html](http://ubuntu.swerdna.org/ububootsuse.html)

[http://www.linuxforums.org/forum/suse-linux-help/156838-dual-boot-opensuse-ubuntu-9-04-a.html](http://www.linuxforums.org/forum/suse-linux-help/156838-dual-boot-opensuse-ubuntu-9-04-a.html)

You can Google for a lot of side by side install instructions and tutorial options too.

Good Luck

---

### Post by stunningman on 2009-12-30
is there any quick fix.

---

### Post by presence1960 on 2009-12-30
> **stunningman said:**
> is there any quick fix.

when you install suse's bootloader (GRUB) install it to the first sector of the open suse installation (/) partition NOT MBR of disk. Then you can add a chainload entry to Jaunty's menu.lst to boot suse

---

### Post by raymondh on 2009-12-30
> **presence1960 said:**
>  install it to the first sector of the open suse installation (/) partition not mbr of disk. Then you can add a chainload entry to jaunty's menu.lst to boot suse

+1

---

### Post by TetonsGulf on 2009-12-31
presence1960 is right, it's the best way.

---

