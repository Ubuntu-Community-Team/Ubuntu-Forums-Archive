---
title: "multiple GRUB boot entries"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by nash black on 2010-04-22
Hi

I just installed Ubuntu 9.10 and a funny thing happened with the GRUB this morning.

First after trying to load GRUB it had an error and stated that it couldnt find a disk or that the disk didn't exist(can't remember the exact words)

I rebooted and it has been loading fine since then but after rebooting there are now duplicate entries for the two Ubuntu options (one normal the other ~safemode-ish one). This isnt a huge issue, but it would be nice to get rid of the extras.

Any idea whats going on with that and how I can get it back to normal?

thanks

---

### Post by Gone fishing on 2010-04-22
Sounds like the kernels updated. Every time it updates you get a new entry you can boot to the old kernels. Its a good idea to keep the last kernel as you can then always boot if an update breaks the system.

Old kernel images can be removed using synaptic and uninstalling the old kernel image.

---

### Post by da burger on 2010-04-22
I assume those are different kernels. The entries in GRUB should have a long number after them and those numbers are probably different. You can remove the old kernels so that there is only one set of entries but I would advise always keeping at least 2 so that you have a plan B if your current kernel has a problem. Could you post the actual entries from the GRUB menu?
Angus

---

### Post by nash black on 2010-04-22
Oh yeah it looks like you're right

two of the entries are: 
Ubuntu, Linux 2.6.31-20 - generic

and the others are:
Ubuntu, Linux 2.6.31-14 - generic

thanks

---

### Post by cuberts on 2010-04-22
> **nash black said:**
> Hi

I just installed Ubuntu 9.10 and a funny thing happened with the GRUB this morning.

First after trying to load GRUB it had an error and stated that it couldnt find a disk or that the disk didn't exist(can't remember the exact words)

I rebooted and it has been loading fine since then but after rebooting there are now duplicate entries for the two Ubuntu options (one normal the other ~safemode-ish one). This isnt a huge issue, but it would be nice to get rid of the extras.

Any idea whats going on with that and how I can get it back to normal?

thanksTo remove these entries, we’ll need to edit the file /boot/grub/menu.lst. You can do this by using Alt+F2 and then typing in the following command:

gksu gedit /boot/grub/menu.lst

[IMG]http://www.howtogeek.com/wp-content/uploads/2007/09/image57.png[/IMG]

---

