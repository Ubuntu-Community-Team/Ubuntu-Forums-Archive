---
title: "ubuntu and gentoo dual boot"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by jackgu1988 on 2009-02-08
hi! i installed gentoo in a partition on my pc and when i reboot my pc it is not on the list... on the list i can only see ubuntu and debian (i used to have debian in a partion but no more)... what can i do? thank u!

---

### Post by pbotros1234 on 2009-02-08
1) Boot up your ubuntu partition

2) open a terminal and type:
```
sudo gedit /boot/grub/menu.lst
```

3) Go to the bottom and add the following:

```
title Gentoo Linux
root (hd0,X) <----------- replace "X" with your partition number - 1 (/dev/sda3 would be (hd0,2))
kernel /boot/bzImage root=/dev/sdaX <----- see below
```

For your "kernel" line, mount and open up your Gentoo partition, and navigate to the "boot" folder in the root of the partition. There should be a file "bzImage" which is your linux kernel for your gentoo partition. If thats true, then you can leave the line as it is.

But if there is no /boot/bzImage on your gentoo partition, you need to find where your kernel is located and change the line according.


EDIT: Just to let you know, Gentoo is an advanced linux distribution and takes a lot of work to set up, so hopefully you know what you're getting in to :)

---

### Post by &#32 Greg on 2009-02-08
Did you do a stage3 (CLI) install of Gentoo, or a stage5 (graphical, from the livecd) install?

---

### Post by jackgu1988 on 2009-02-08
> **  Greg said:**
> Did you do a stage3 (CLI) install of Gentoo, or a stage5 (graphical, from the livecd) install?

i did a graphical install...

---

### Post by jackgu1988 on 2009-02-08
i did it and when gentoo loads there is another problem! it says:

> VFS: Cannot open root device "sda8" or unknown-block(0,0)
Please append and correct "root=" boot option; here are the available partitions:
0b00    1048575 sr0 driver: sr
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
i sense something is going wrong... :p

---

