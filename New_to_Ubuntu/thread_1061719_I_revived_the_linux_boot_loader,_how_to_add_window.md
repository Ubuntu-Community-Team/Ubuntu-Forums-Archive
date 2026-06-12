---
title: "I revived the linux boot loader, how to add windows to boot list again?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by legolas_w on 2009-02-06
hi
thank you for reading my post
I revived my linux boot loader but I can not understand how to add the windows menu item to it.
I opened the menu.lst and also Here is the result of fdisk -l

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x29f418d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15501   117187528+  83  Linux
/dev/sda2   *       15502       15529      204800    7  HPFS/NTFS
/dev/sda3           15529       20674    38896640    7  HPFS/NTFS


```

can you pleas let me know what to add in menu.lst to make it work?
I have installed windows 7 beta which caused the boot menu to be gone.
thanks.

---

### Post by hyper_ch on 2009-02-06
[http://tinyurl.com/d7wlqh](http://tinyurl.com/d7wlqh)

---

