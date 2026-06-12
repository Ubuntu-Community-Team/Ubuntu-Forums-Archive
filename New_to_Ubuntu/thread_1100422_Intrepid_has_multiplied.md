---
title: "Intrepid has multiplied"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by nnjond on 2009-03-19
Hi, my os prompted me to restart after a dl; Now the grub menu show me 6 options of 8.10 + recovery modes, but openSuse option has dissappeard.

Do i really need 6  on a grub menu? What does this mean?

---

### Post by mikewhatever on 2009-03-19
That was a kernel update. When performed, the older kernel and the rgub entry are not removed, so that you could choose to boot it at will.
As for OpenSuse's entry, it must have been placed inside the Debian Kernels section and got overwritten since it didn't belong there in the first place.

---

### Post by tarps87 on 2009-03-19
Each entry is probably a different kernel version with normal and recovery mode.
e.g.
***** kernel 2.6.27.7-generic
***** kernel 2.6.27.7-generic (recovery mode)
***** kernel 2.6.27.9-generic
***** kernel 2.6.27.9-generic (recovery mode)
***** kernel 2.6.27.11-generic
***** kernel 2.6.27.11-generic (recovery mode)

You can delete the old options from the menu.lst if you no longer use them. They are there in case the latest kernel does not work with the hardware for some reason or other, you will still be able to boot using the old one.

You may find this useful
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

About the openSuse option, this may be due to the option you selected after the kernel update, it will have asked you what boot list/menu.lst you want to use. The old one should be labled menu.lst.bck in /boot/grub/
If you post the contents of the two file I can look and see if it is there
```
sudo cat /boot/grub/menu.lst
sudo cat /boot/grub/menu.lst.bck
```

---

### Post by mikewhatever on 2009-03-19
Actually, deleting a kernel entry from the menu.lst file wouldn't remove the file from the HDD. You should remove the file and the menu.lst gets update in the process.

---

### Post by pdoma on 2009-03-19
As Tarps87 said, you can aither modify the /boot/grup/menu.lst or if you're not up to seepd with edditing text you can install StartUP Manager (a user friendly application for managing the way your PC boots up) and change it in there.

Good luck.

---

### Post by tarps87 on 2009-03-19
> **mikewhatever said:**
> 
As for OpenSuse's entry, it must have been placed inside the Debian Kernels section and got overwritten since it didn't belong there in the first place.

So that's how it works it out, thanks

> **mikewhatever said:**
> Actually, deleting a kernel entry from the menu.lst file wouldn't remove the file from the HDD. You should remove the file and the menu.lst gets update in the process.

I tend to just delete the entry unless I'm running out of space, that way I have a backup if I really need it, but it would be better to do it that way

By the way isn't your signature wrong? Shouldn't it be windows is NOT Linux :)

---

### Post by nnjond on 2009-03-19
Thanks everyone. I now see I can scroll down to the Os os

---

### Post by snkiz on 2009-03-19
personally I like to keep the last kernel before the update and remove the rest. Keeps my grub tidy, and I have an easy access backup when things go wrong.

---

