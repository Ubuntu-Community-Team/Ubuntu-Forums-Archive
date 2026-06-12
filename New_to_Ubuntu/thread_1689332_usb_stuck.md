---
title: "usb stuck"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by bjje on 2011-02-16
I run 10.10, put in a usb stick and it shows up on the desktop. It shows up in /dev but I can't write to it. I can't even unmount it, giving me;

umount: /media/usb0 is not in the fstab (and you are not root)

 I find that I can sudo cp to it, so I change owner and permissions but gnome still cannot do anything with it. what have I missed?

---

### Post by sikander3786 on 2011-02-16
[s]Changing the ownership and permission of system files and directories hurts the Operating System in most cases and it starts acting weird.

How was the USB prepared and how did you chown/chmod?[/s]

Sorry for the irrelevant reply. Please see *quadproc's* suggestions in the post below.

---

### Post by quadproc on 2011-02-16
> **bjje said:**
> I run 10.10, put in a usb stick and it shows up on the desktop. It shows up in /dev but I can't write to it. I can't even unmount it, giving me;

umount: /media/usb0 is not in the fstab (and you are not root)

You need to be root to umount something, and that something has to be not in use.  So, if your USB stick has been automounted by the OS you will need to umount it first.  You can get a list of mounted devices by inputting
```
mount
```from a terminal.

Note that cd to the stick makes it in use so you'll have to cd to somewhere else to avoid this trap.

quadproc

---

### Post by bjje on 2011-02-16
Yes, I can unmount it in terminal but still can't get gnome to use it.

---

### Post by TeoBigusGeekus on 2011-02-16
Mount it and post us the output of
```
mount
```
from terminal.

---

### Post by quadproc on 2011-02-16
> **bjje said:**
> Yes, I can unmount it in terminal but still can't get gnome to use it.
I am not sure what you mean - did you try to read it or write it while it was unmounted?  If so, that attempt should fail.  To be able to read or write such a device, it needs to be mounted and the permissions need to be sufficient to allow you access.  Or, you need to have root privilege.

quadproc

---

