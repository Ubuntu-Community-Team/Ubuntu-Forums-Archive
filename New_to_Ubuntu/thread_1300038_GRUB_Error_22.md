---
title: "GRUB Error 22"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by burtzacarach on 2009-10-24
I have two drives in my system in a master-slave configuration, on the master drive there is an installation on Windows XP and an install of Ubuntu and they had both worked fine, but then I installed Ubuntu onto the slave drive with the bootloader option at (hd0) and now I can't boot from either drive. When I try to boot from the master drive, I get a GRUB Error 22, and when I try to boot from the slave drive, I get "F1 to retry boot, F2 for BIOS options" or something of the like. My heart skipped a beat when this happened and I'm not sure what to do!
Does anyone have any ideas on how to correct this?
Yikes!

---

### Post by ranch hand on 2009-10-24
First boot from your LiveCD and make sure that the OS' are where you think they are.  They probably are.

Still on the CD got to terminal and;
```

sudo grub

```
You will get a series of grub prompts ("grub>").
At these  prompts run these commands;
```

find /boot/grub/stage1
root (hd1,0)
setup (hd0)
quit

```
This is assuming some things.
First that the find command comes up with the same "(hd1,0)" that I guessed at.  If not use what is there.
Second that you want to boot from the mbr of the first drive.
Third that you "moved" by way of installing and transfering your data to the second drive.

If you copied your partition(s) to the second drive you need to go in, from the live CD and edit your /etc/fstab file before doing anything else.

---

