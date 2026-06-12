---
title: "space reserved for virtual system"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by libihero on 2009-07-15
is it possible to decrease the amount of space reserved for my virtual system on virtual box?

---

### Post by Delever on 2009-07-15
It is probably not worth the effort, but might be done like this:

1. Create another smaller disk. Assign this smaller disk to virtual machine.
2. Load LiveCD in your VBox. Open Partition Editor, resize your current partition, then copy all partitions to another disk.
3. Shut down, detach larger disk, then load LiveCD again (or Windows CD). Fix boot loader (Win7 would do this automatically, other versions - google it) or grub (instructions bellow).
4. You should be able to load your system.

To fix grub:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

But probably it would be faster to reinstall.

---

