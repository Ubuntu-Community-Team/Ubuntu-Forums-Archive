---
title: "Grub Ubuntu/Windows Dual Boot"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Enjeru on 2008-12-13
Hey guys,

I dual boot into Windows XP occasionally to play games that don't run under wine using the following lines in /boot/grub/menu.lst:

```

title		Windows XP
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify 	(hd1,0)
chainloader +1
```

I have 2 hard drives in my laptop and XP is on the second.  I was wondering if it was possible to move all of XP into a different folder other than root on hd1 (so I could organize the things inside that drive better) and still boot from XP.  (i.e. I want to move windows from "/" to "/Windows XP/")

---

### Post by logos34 on 2008-12-13
you want to move the entire xp partition to another one on the same disk?  If that's what you mean, then yes.  For ex, if you moved to the second partition, you would change menu.lst entry to:
> 
rootnoverify 	(hd1,[COLOR="Red"]1[/COLOR])

---

### Post by jbrown96 on 2008-12-13
> **Enjeru said:**
> Hey guys,

I dual boot into Windows XP occasionally to play games that don't run under wine using the following lines in /boot/grub/menu.lst:

```

title		Windows XP
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify 	(hd1,0)
chainloader +1
```

I have 2 hard drives in my laptop and XP is on the second.  I was wondering if it was possible to move all of XP into a different folder other than root on hd1 (so I could organize the things inside that drive better) and still boot from XP.  (i.e. I want to move windows from "/" to "/Windows XP/")

I don't really understand what you are trying to do; could you post the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```? I'm not sure how much Windows will like being moved. To update grub you just need to know the partition and disk. Once you get everything moved around run ```
sudo fdisk -l
``` again. Find you XP parition, you then need to know the device name and parition number. /dev/sda1 is the first disk (the "a") and first partition ("1"), /dev/sdb1 is the second disk ("b") and first parition ("1"), /dev/sda2 is first disk and second parition. Update te grub rootnotify part of the grub entry. (hd1, 0) is the second device (hd1) and first partition (0). The first device is (hd0). Everything should work properly.

---

### Post by Enjeru on 2008-12-14
No see what I meant is that I have bunch of other stuff on that partition other than XP and I want to make it so all of XP sits inside a folder and not the root of the drive (which I suppose would effectively change the "root" that XP sees/runs from - like (hd1, 0, /Windows XP) assuming that was command).

---

### Post by logos34 on 2008-12-14
> **Enjeru said:**
> No see what I meant is that I have bunch of other stuff on that partition other than XP and I want to make it so all of XP sits inside a folder and not the root of the drive (which I suppose would effectively change the "root" that XP sees/runs from - like (hd1, 0, /Windows XP) assuming that was command).

you could make a new partition and copy/move all of "My Documents", games and installed programs and apps to it, leaving only XP system files on C: (the new partition would likely be seen as D: drive).  You wouldn't have to change anything in grub--you'd still boot windows C: (hd1,0).  But you'd need to add a new mount point in ubuntu for the new partition.

---

