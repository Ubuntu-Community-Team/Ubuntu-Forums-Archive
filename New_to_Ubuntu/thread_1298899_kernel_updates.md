---
title: "kernel updates"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by jmundinger on 2009-10-23
Yesterday, I updated Ubuntu.  Among other things, the update included a new kernel.  I am now operating from 2.6.28-16-generic.  Two earlier versions ( -11 and -15) also show up in GRUB and, I assume, are still on my system.  What is the recommended procedure for managing older versions of the kernel when the kernel is updated?  I presume they should be kept for awhile to allow the user to revert in case there are issues with the newer version.  But, how long should they be kept and what is the appropriate procedure for removing them?

---

### Post by ukripper on 2009-10-23
You can safely remove your old kernels once you are satisfied new kernel update didn't mess up anything. there is no time restriction for it. Check this link for more info [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

you can also limit what your grub shows you  in menu.lst.

---

### Post by jmundinger on 2009-10-23
Thanks.  That was painless...I think.:)

---

### Post by sinbin on 2009-10-23
> **ukripper said:**
> You can safely remove your old kernels once you are satisfied new kernel update didn't mess up anything. there is no time restriction for it. Check this link for more info [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

you can also limit what your grub shows you  in menu.lst.

Thank you for this information. This one is a valuable lesson!:)

---

