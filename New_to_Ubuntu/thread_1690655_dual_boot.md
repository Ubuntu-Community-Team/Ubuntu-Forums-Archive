---
title: "dual boot"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by lahrs on 2011-02-18
I'm trying to dual boot mint 10 and ubuntu 10.04. The installation went fine but I am unable to choose between the two systems. Newbie.  Please help

---

### Post by ianc1 on 2011-02-18
What options do you see?

On my Ubuntu/Windows dual boot I see 4 Ubuntu options can't remember the exact wordings but they are for normal use of latest kernel I and others such as booting into the terminal mode.  At the end of the list I see various windows options the last of which starts Windows I believe the others are areas where the recovery software etc are stored.

Is it possible you wiped the Ubuntu with the Linux did you do a side-by-side install or your own partitioning?

---

### Post by wilee-nilee on 2011-02-18
If you thnk you have overwritten the original, and to be safe boot the live mint cd and run this command and post it.
fdisk -l

---

### Post by Hippytaff on 2011-02-18
how do you mean you are unable to choose between the two systems?

Try booting form a livecd/usb...opening a terminal CTRL+ALT+T and doing```
 sudo update-grub
```

---

### Post by wilee-nilee on 2011-02-18
> **Hippytaff said:**
> how do you mean you are unable to choose between the two systems?

Try booting form a livecd/usb...opening a terminal CTRL+ALT+T and doing```
 sudo update-grub
```

Has to be done from the install.:)

---

