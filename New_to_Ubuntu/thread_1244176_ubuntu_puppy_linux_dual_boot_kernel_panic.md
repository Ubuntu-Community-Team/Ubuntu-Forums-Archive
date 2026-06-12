---
title: "ubuntu/ puppy linux dual boot kernel panic"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-08-19
Hi

I partitioned my HD into two sections (and a swap) and then installed puppy linux onto /dev/sda3
I then added the following instruction (from the final part of the puppy install process) to the bottom of /boot/grub/menu.lst and saved:

title          Puppy Linux 421 full install on sda3
root          (hd0,2)
kernel       /boot/vmlinuz root=/dev/dsa3 pmedia=atahd nosmp
      
when pressing esc on grub loading the Puppy Linux 421 full install on sda 3 is there but when selected this happens:

Unlzmaing Linux.........done
Booting the kernel
init: applet not found
kernel panic - not syncing:
Attempting to kill init!

Any ideas what the problem is here?
Thanks

---

### Post by mike555 on 2009-08-19
Did you install grub for puppy to the beginning of it's partition ? I think it needs it to start even though you have grub at startup.

---

### Post by Duke Togo on 2009-08-20
no I didn`t
how would I go about that?

---

### Post by mike555 on 2009-08-20
During the installation it should have asked you about where you wanted to install grub ...... if you did a full install ...

---

