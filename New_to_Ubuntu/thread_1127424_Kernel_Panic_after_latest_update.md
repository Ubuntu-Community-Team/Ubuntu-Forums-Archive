---
title: "Kernel Panic after latest update"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by betacorpo on 2009-04-16
Hi forum

I did the latest update (On April 16 2009) and my computer will not reboot - it hangs on this message

kernel panic - not synching attempt to kill init

how do i recover the operating system?  what happened?

thanks

---

### Post by nnarayann on 2009-04-16
Hi!!. I've just read some things you might want to try:

[I]Boot to the liveCD, open a terminal and run:

sudo badblocks -v /dev/sda

That will scan your drive for bad spots. You also might want to scan the filesystem. Assuming your root filesystem is /dev/sda1, you'd run:

sudo fsck /dev/sda1

Another option is to try booting into the recovery mode (second option in grub). Also, if you have a second kernel from previous system updates, try booting into them.[/I]

Good luck.

nnarayann.

---

