---
title: "Where has Win XP gone?"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by TideMan on 2009-03-12
We have an old PC with 256 MB RAM that was running Win XP, but like a dog. So I installed Xubuntu 8.10, expecting to be able to dual boot.

Everything went fine during installation.  The installation detected the Win XP portion of the disk and showed me how it was going to install Xubuntu in the other bit, so I proceeded.

But now, when I boot up, I don't get an option to go to Win XP.  It goes straight into Xubuntu.

I fear I have lost Win XP and all the files that were there, but I'm hoping not.

Can someone tell me how I can check this?  I don't seem to be able to see anything on the disk except Linux folders.

Incidentally, Xubuntu works fine and is much faster than Win XP was.  The main thing is that the HD doesn't click and clack and whine continuously, as it did with Win XP.

---

### Post by st33med on 2009-03-12
> **TideMan said:**
> We have an old PC with 256 MB RAM that was running Win XP, but like a dog. So I installed Xubuntu 8.10, expecting to be able to dual boot.

Everything went fine during installation.  The installation detected the Win XP portion of the disk and showed me how it was going to install Xubuntu in the other bit, so I proceeded.

But now, when I boot up, I don't get an option to go to Win XP.  It goes straight into Xubuntu.

I fear I have lost Win XP and all the files that were there, but I'm hoping not.

Can someone tell me how I can check this?  I don't seem to be able to see anything on the disk except Linux folders.

Incidentally, Xubuntu works fine and is much faster than Win XP was.  The main thing is that the HD doesn't click and clack and whine continuously, as it did with Win XP.

Hit escape when you see that countdown timer.  You'll go back to the menu.

---

### Post by TideMan on 2009-03-12
No, I tried hitting Esc, but it ignores me.
It counts down from 3 to 0 and boots straight into Xubuntu.

---

### Post by 73ckn797 on 2009-03-12
Will need to see how the "menu.lst" is written.

Open Terminal and type:

```
sudo mousepad /boot/grub/menu.lst
```

(I do not have Xubuntu running on this computer so the command may be incorrect)

Post the last section that lists operating system(s) choices.

---

### Post by rafac24 on 2009-03-12
If you want to install mousepad, then by all means. May be easier just to run with gedit:

```
sudo gedit /boot/grub/menu.lst
```

That's an 'L' not a number 1.

---

### Post by rafac24 on 2009-03-12
Disregard that. Forgot to read that you were running Xubuntu.

:(

---

### Post by TideMan on 2009-03-12
Oh dear, this is what mousepad says:
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		7f80076d-8014-4d92-9bfc-60b1eb616409
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7f80076d-8014-4d92-9bfc-60b1eb616409 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7f80076d-8014-4d92-9bfc-60b1eb616409
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7f80076d-8014-4d92-9bfc-60b1eb616409 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7f80076d-8014-4d92-9bfc-60b1eb616409
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7f80076d-8014-4d92-9bfc-60b1eb616409 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7f80076d-8014-4d92-9bfc-60b1eb616409
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7f80076d-8014-4d92-9bfc-60b1eb616409 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7f80076d-8014-4d92-9bfc-60b1eb616409
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by PukingPenguin on 2009-03-12
before mucking about with your menu.lst any further, let's see the output of ```
sudo fdisk -l
```This will help us to determine if Windows is even extant anymore....

---

### Post by TideMan on 2009-03-12
Output from sudo fdisk -l:
```
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb711b711

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4774    38347123+  83  Linux
/dev/sda2            4775        4866      738990    5  Extended
/dev/sda5            4775        4866      738958+  82  Linux swap / Solaris
```

---

### Post by 73ckn797 on 2009-03-13
Your posting of "fdisk -l" shows no Windows partition at all. You appear to not have Windows any more.

---

