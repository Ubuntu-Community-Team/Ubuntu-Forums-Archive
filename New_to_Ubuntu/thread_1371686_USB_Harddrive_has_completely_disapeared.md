---
title: "USB Harddrive has completely disapeared"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2010-01-03
I recently reformatted my USB 2.0 WD 1 Terrabyte hard drive to ext3 with
```

sudo mkfs.ext3 -I 128 -L "wdtb" /dev/sdb1

```

I mounted it in a windows XP Virtual machine (VirtualBox 3.1.2) and mounted with ext2ifs.
I shutdown the virtual machine and have since not  been able to see the drive.
I rebooted and did

```
sudo fdisk -l
```

...and nothing.
I tried
```
lsusb
```
...not there.

this drive is about a year and a half 

old but wasn't very heavily used.

I even tried testdisk...It didn't see it.
Ubuntu folks are quite smart and I was hoping that someone here could lend me a hand.

---

### Post by J V on 2010-01-03
Can you see it in gparted? (always use gparted for formatting)

---

### Post by JohnGalt131 on 2010-01-03
no I cannot. I usually use gparted. However, I don't know how to specify inode size in gparted.

---

### Post by J V on 2010-01-03
Well if you can't see it in gparted, can you see it in windows?

If its not in gparted it seems you are screwed...

---

### Post by JohnGalt131 on 2010-01-03
> **J V said:**
> Well if you can't see it in gparted, can you see it in windows?

If its not in gparted it seems you are screwed...

I'm afraid I don't see it in windows either. I didn't realize a harddrive could just disappear. I know it isn't lack of power, since the drive is spinning. I know it isn't the coord, I've swapped them.

---

### Post by JohnGalt131 on 2010-01-03
Very weird. I unplugged the power source waited a few minutes, and plugged it back in and STRANGELY it mounted fine. I am baffled. Thanks anyways guys.

---

