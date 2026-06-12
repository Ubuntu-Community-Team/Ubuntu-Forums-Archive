---
title: "Ubuntu+Element OS+Open SUSE"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by TheGuyBehindTheGuy on 2010-10-02
Ok, now that my first problem is done, I'll work on the second problem: Tri-boot. My goal is to put Ubuntu, Element OS, and Open SUSE all on the same external harddrive with a home folder. I have tried before, which is how my first problem came to be, and now I'm gonna ask for pro help. Any advice? \\:D/

---

### Post by cariboo on 2010-10-03
The last distribution you install will be the one that installs grub in the mbr. I would suggest you install grub on the mbr of the external hard drive, that way it will have no effect on whatever is on the main hard drive.

Setup your system to boot from usb first, that way it will boot from your external drive, when it's connected, and from the main hard drive when it isn't connected.

Ubuntu now uses Grub2 where as Element OS and openSUSE both use grub-legacy, this shouldn't be a problem, but be aware of it.

---

### Post by TheGuyBehindTheGuy on 2010-10-04
So, basically what do I do? Install Element, OpenSUSE, then ubuntu? Do I create partitions before or during installation?  How do I create a home folder? :-k

---

