---
title: "boot default"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Possom on 2009-07-12
On my Hardy dual boot system how can I set the grub default such that unattended boot selects a specific OS?

---

### Post by ChrisB111 on 2009-07-12
Grub uses the menu.lst file for its configuration, open this file by going:
```
gksudo gedit /boot/grub/menu.lst
```
You can either then change the default property to the number of the boot option or change the order of the boot options so the default is at the top.

Chris

---

### Post by LewRockwell on 2009-07-12
> **Possom said:**
> On my Hardy dual boot system how can I set the grub default such that unattended boot selects a specific OS?

edit the menu.lst

please be advised that there are already hundreds of internet-available tutorials/articles/threads/posts on editing the grub...so we won't try to re-invent the wheel here...

hopefully this makes sense...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) has helped some people do some tasks(we wouldn't be caught without a supergrubdisk onhand, if that's any indication of it's worth)

.

---

### Post by northern lights on 2009-07-12
You have to edit's GRUB's (your bootloader's) options.

From within your Hardy, run```
gksu gedit /boot/grub/menu.lst
```either from the Terminal or the Alt+F2 dialog.

You have two options to accomplish what you want.

Either locate the following entry near the top```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```and adjust the number (i.e. what now is 0) to the appropriate boot option - if Windows is the fifth entry in the GRUB menu, make it 4.

Or leave this section as is and cut/paste the Windows entry ```
title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1
```(similar to the above, located near the bottom) to the top of the menu, i.e above the entry similar to
```
title		Ubuntu 8.04, kernel 2.6.2X-XX-generic
uuid		27c731a2-850e-44b6-9dc7-bad0378fcd0c
kernel		/boot/vmlinuz-2.6.2X-XX-generic root=UUID=27c731a2-850e-44b6-9dc7-bad0378fcd0c ro quiet splash 
initrd		/boot/initrd.img-2.6.2X-XX-generic
quiet
```and below```
## ## End Default Options ##
```

---

### Post by LewRockwell on 2009-07-12
ok, ok...

read this FIRST!
[http://ubuntuforums.org/showthread.php?t=854820](http://ubuntuforums.org/showthread.php?t=854820)

and, since you've been directed to initiate an active read AND WRITE editing session...sigh...

do this FIRST!```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```

.

---

### Post by Possom on 2009-07-13
Thanks to all, suggestions worked great!

---

