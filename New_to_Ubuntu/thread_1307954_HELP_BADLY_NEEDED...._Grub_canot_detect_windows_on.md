---
title: "HELP BADLY NEEDED.... Grub canot detect windows on startup boot"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by resume on 2009-10-31
HI to all...

i am a newbie wen it comes to ubuntu need your technical help..

scenario:

I've installed a XP professional on my MSI x320 laptop. i decided to have a 20gb partition on a NTFS. and decided to try the new 9.10 ubuntu. I've installed it successfully but windows doesn't appear/detect on GRUB... i've tried to read other threads but still i cannot do it. can someone explain to me in details... tnx in advance..

PS: i've run a FDISK on terminal and this is what it appears

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe15ad4d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19457   135805477+   5  Extended
/dev/sda5            2551       18765   130246956   83  Linux
/dev/sda6           18766       19457     5558458+   7  HPFS/NTFS

---

### Post by Liolikas on 2009-10-31
No real problem we will fix this manually.

Show /boot/grub/menu.lst too.
cat /boot/grub/menu.lst

---

### Post by kansasnoob on 2009-10-31
Fresh installs of Karmic have no menu.lst.

Just try running:

```
sudo update-grub
```

---

### Post by resume on 2009-10-31
tried dat to edit also.
title Microsoft XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

that's all that shows. i think i've accidentaly removed/replaced the orginal one?!?!? don't know..

---

### Post by kansasnoob on 2009-10-31
> **resume said:**
> tried dat to edit also.
title Microsoft XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

that's all that shows. i think i've accidentaly removed/replaced the orginal one?!?!? don't know..

What file did you edit?

---

### Post by kansasnoob on 2009-10-31
Post the output of:

```
grub-install -v
```

and:

```
ls ~ /boot/grub
```

---

### Post by resume on 2009-10-31
@kansas noob i've tried it and it works... how could I edit the boot menu (i want to remove like the recovery and memtest) and the default time.

---

### Post by resume on 2009-10-31
the menu.lst but no worries it works fine now

---

### Post by emigrant on 2009-10-31
> **resume said:**
> @kansas noob i've tried it and it works... how could I edit the boot menu (i want to remove like the recovery and memtest) and the default time.

```
sudo gedit /boot/grub/menu.lst
```

and put '#' infront of everything you don't want (to comment):

```
#title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid            becef1b2-d864-4764-828f-6381e90fd95d
#kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=becef1b2-d864-4764-828f-6381e90fd95d ro  single
#initrd          /boot/initrd.img-2.6.28-11-generic

#title           Ubuntu 9.04, memtest86+
#uuid            becef1b2-d864-4764-828f-6381e90fd95d
#kernel          /boot/memtest86+.bin
#quiet

```

---

### Post by kansasnoob on 2009-10-31
Grub 2 is a different animal:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by resume on 2009-10-31
@kansasnoob

tnx.. i'm using 1.9beta4 version do you think i should upgrade?

---

### Post by kansasnoob on 2009-10-31
1.97beta4 is the latest version.

But there should be no menu.lst.

---

### Post by jrrader on 2009-10-31
I think it's possible that he may have created a menu.lst in the process of trying to get this to work.  It could exist, but it wouldn't be doing anything but sitting in the directory.

---

