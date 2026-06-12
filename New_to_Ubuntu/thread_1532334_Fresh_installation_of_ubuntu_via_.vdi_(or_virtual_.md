---
title: "Fresh installation of ubuntu via .vdi (or virtual image) file"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by rohan2k10 on 2010-07-16
Can we install ubuntu on a new machine using the virtual os image.

I have virtual box images that i want to use to install ubuntu server on a  fresh Harddisk.

Is this possible to do.  

Please suggest.

---

### Post by eriktheblu on 2010-07-16
I'm not an authority on this topic but I'm pretty sure it's either impossible, or not worthwhile.

I suggest downloading and burning the install CD.

---

### Post by Ocxic on 2010-07-16
you can try it, what i would do is boot a your virtual machine with live CD, and use "dd" to copy the disk to an image file. then copy that image to your hard disk with dd again, and boot.

---

### Post by tarps87 on 2010-07-16
> **Ocxic said:**
> you can try it, what i would do is boot a your virtual machine with live CD, and use "dd" to copy the disk to an image file. then copy that image to your hard disk with dd again, and boot.

This is the logical way and with the exception of the MBR should work relying on the virtual hard drive being equal or smaller than the physical one you are copying to

---

