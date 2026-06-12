---
title: "Removing Ubuntu from second SSD on eeePC"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Sunnieboy on 2009-02-15
I have just started with an eeePC 1000 with two SSD 8G and 32G. Xandros was preinstalled on the 8G SSD and I used Ubuntu Live CD 8.10 to install Ubuntu on the 32G SSD to compare.

Now decided Ubuntu's for me and so then installed 8.10 onto the 8G SSD but still have a copy on the 32G SSD Grub allows me to boot to either drive but I now want to remove 8.10 from the 32G SSD. Any advice or pointers on best way to do this, Gparted, delete via File Manager, uninstal (if so how)

Regards

Sunnie

---

### Post by andrewc6l on 2009-02-15
If you delete the reference to Ubuntu 8.10 on the 32G SSD from your /boot/grub/menu.lst, you should be free to do what you want with the 32G hard drive... including just nuking it, partitioning it to hold another OS, mounting it as another drive on your filesystem, etc.

Be careful, though - if you delete the wrong one, your 8G SSD won't be bootable. Probably best to back up the original to USB flash drive or something handy.

---

### Post by Sunnieboy on 2009-02-16
Andrew

Thanks will try to remove from the boot list and then reformat the second SSD

Sunnie

---

