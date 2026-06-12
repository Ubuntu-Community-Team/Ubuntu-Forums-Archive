---
title: "[SOLVED] Resizing Ubuntu Partion"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by bbright20 on 2008-12-09
I have just recently installed Ubuntu 8.10 and I am loving it. I have an 80gb hdd with a dual boot Windows Xp and Ubuntu 8.10. I only made 15gb for Ubuntu and the rest is XP. I was wondering if there was a way that I could resize my Ubuntu partition. I know how to shrink my XP partition. How can I increase the size of my Ubuntu partion? XP is the primary and Ubuntu is the logical.

---

### Post by Moop on 2008-12-09
I doubt you would ever need more than 15gb for ubuntu and you can always use your windows partition for storage etc. 

But you can change the size of your partitions using the live cd and gparted. It's always best to have things backed up before resizing partitions.

---

### Post by earthpigg on 2008-12-09
easiest way is to use gparted

```
sudo apt-get install gparted
```

to run it, 

```
sudo gparted
```

its got a very easy to use GUI.

naturally, you should back up everything on your computer prior to resizing partitions.

---

### Post by bbright20 on 2008-12-09
Thanks for all the info.

---

### Post by mikewhatever on 2008-12-09
It can be done using the Gparted live cd or another live cd with a similar program, but that is only part of the deal. If a partition is resized, it's uuid is changed and you'd need to edit /boot/grub/menu.lst and /etc/fstab to successfully boot Ubuntu. You can find out the new uuid with <sudo blkid> command.

The reason you have to use a live cd is that when Ubuntu runs it's partition is mounted, and you can't resize a mounted partition, nor can you unmount the system partition while the OS is running.
In short, it's not rocket science, but may be a bit intimidating.

---

### Post by earthpigg on 2008-12-09
ah, forgot that part!

---

