---
title: "Update kernel version in boot list"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by nebu on 2009-06-23
I use Ubuntu 9.04 64bit edition.....

I recently downloaded the 2.6.28-13 kernel....

but my grub menu.lst file still boots of the old 2.6.28-11 kernel version.... 

how do i change it to the new 2.6.28-13 version?

---

### Post by 73ckn797 on 2009-06-23
Does /boot/grub/menu.lst have the new kernel listed?

You could open terminal and enter:
```
sudo /boot/grub/menu.lst
```Once there you could just copy and paste the choices then change kernel references to the new version. You can keep the older kernel in the list in case the new one causes any problems. You would then be able to boot using the old kernel.

The other simple option would be to change the kernel number to 13 from 11.

Here is what mine looks like. You would not have the same uuid number but this is what it could look like:```

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        4bf4c56b-3c79-442e-b6ee-86eadaf4f7ea
kernel        /boot/memtest86+.bin
quiet
```

The first line of each section is only the title. You would also need to change all other kernel numbers.

---

### Post by nebu on 2009-06-23
will there be any change in the boot parameters?

---

### Post by freak42 on 2009-06-23
you should issue the following command instead of manually updating 
your menu.lst

sudo update-grub

it will generate a new menu.lst file with your newest kernel.

---

### Post by 73ckn797 on 2009-06-23
> **freak42 said:**
> you should issue the following command instead of manually updating 
your menu.lst

sudo update-grub

it will generate a new menu.lst file with your newest kernel.


There, you have it even easier.

---

