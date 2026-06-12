---
title: "Cannot access after wiping disk"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by SteelCore on 2010-03-16
I have 4 hard disks on my system each with several installations of 9.10.
Today I wiped sdd with (dd if=/dev/zero of=/dev/sdd). Since the Ubuntus on sdd were installed last I assumed wiping them won't affect the boot loader. Seems I was very wrong. Now I can't access the system. After booting I get this message.
```
GRUB loading.
error: no such disk
grub rescue> _
```
I'd appreciate any help on this.

---

### Post by I8NY on 2010-03-16
There is a live cd called Super Grub Disc and that will boot the newest Linux kernel on the HDD so you can get the OS running if Ubuntu is installed else where, i don't know if it works with Windows.  I would backup and reinstall grub if you get Ubuntu working again and that should fix the grub error.

---

