---
title: "dual boot ?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by stans on 2009-10-16
I'd like to install OpenSolaris on a separate hard drive and use dual boot to access it. 

Currently have Karmic installed on a 500gb drive and have an unused 200gb drive so do not really need to partition the drive that Ubuntu is on. 

I've searched this forum and see that dual boot usually involves a single drive... so where can I find information that will assist me ?

---

### Post by pythonscript on 2009-10-16
If you partition a single disk, you should be able to install Solaris in that space and it will recognize your ubuntu installation. If grub (which I assume you're using?) gets a few messed up entries, you can either correct them by booting from a live CD or by booting into Solaris and mounting your ubuntu partitions. 

If you don't want to install Solaris on the same drive, you can install it on the second drive and (I hope I have this right) chainload grub from the first disk/second disk to point to grub, or whatever bootloader you're using for Solaris, on the second drive. Look up loading grub on two hard drives for find more. Sorry I don't have any links at the moment; I don't remember where I had the information to set mine up.

---

### Post by stans on 2009-10-16
Thanks for getting back pythonscript...

---

