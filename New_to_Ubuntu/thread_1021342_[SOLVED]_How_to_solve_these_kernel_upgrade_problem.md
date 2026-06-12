---
title: "[SOLVED] How to solve these kernel upgrade problems using &amp;quot;aptitude full-upgrade&amp;quot;?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by AncientPC on 2008-12-25
When running "sudo aptitude -y full-upgrade" the output is below:
```
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following partially installed packages will be configured:
  linux-generic linux-image-2.6.27-7-generic linux-image-2.6.27-9-generic 
  linux-image-generic linux-restricted-modules-2.6.27-9-generic 
  linux-restricted-modules-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.27-7-generic (2.6.27-7.16) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.27-7.14 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.27-7.14 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-9-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-9-generic:
 linux-restricted-modules-2.6.27-9-generic depends on linux-image-2.6.27-9-generic; however:
  Package linux-image-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-9-generic; however:
  Package linux-image-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-9-generic; however:
  Package linux-restricted-modules-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.9.13); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.9.13); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
 linux-image-2.6.27-9-generic
 linux-restricted-modules-2.6.27-9-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
Setting up linux-image-2.6.27-7-generic (2.6.27-7.16) ...
Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
```

---

### Post by zvacet on 2008-12-25
```
sudo dpkg --configure -a
```

---

### Post by AncientPC on 2008-12-25
`sudo dpkg --configure -a` results (it fails with the same errors as aptitude):
```
Setting up linux-image-2.6.27-7-generic (2.6.27-7.16) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.27-7.14 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.27-7.14 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-9-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-9-generic:
 linux-restricted-modules-2.6.27-9-generic depends on linux-image-2.6.27-9-generic; however:
  Package linux-image-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-9-generic; however:
  Package linux-image-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-9-generic; however:
  Package linux-restricted-modules-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.9.13); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.9.13); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
 linux-image-2.6.27-9-generic
 linux-restricted-modules-2.6.27-9-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

```

---

### Post by AncientPC on 2008-12-25
I found the source of the error: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193439](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193439)

Changed my /boot/grub/menu.lst back from default to 0 to fix the error.

---

### Post by bryncoles on 2009-02-14
sorry to jump on a solved thread, but im having a problem with this as well, it might be similar but i do not for the life of me understand what you have done to solve this problem!

what does > Changed my /boot/grub/menu.lst back from default to 0 to fix the error.  actually mean, and how do i do it? (im scared of editing that file and borking my system!

---

### Post by philinux on 2009-02-14
> **bryncoles said:**
> sorry to jump on a solved thread, but im having a problem with this as well, it might be similar but i do not for the life of me understand what you have done to solve this problem!

what does  actually mean, and how do i do it? (im scared of editing that file and borking my system!

A **similar** problem might have a completely different solution. Why not post a new thread with the exact problem you've got.

---

### Post by bryncoles on 2009-02-14
you make a good point! i was just wondering if this would do me any good... its probably better etiquette to use ones own thread for problems anyway!

;)

---

