---
title: "Grub, where is Win XP?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-07-04
Hello, I first installed Ubuntu then after a while did I also install Win XP, since XP is so nice to overwrite mbr was i forced to restore grub. Here is where the problem start I did restore grub but I did the mistake using setup (hd0,0) when I first tried to restore it instead of setup (hd0) that I did use the second time. I guess this is what caused this problem that Xp don't show up in the grub boot list even if I know that it's installed. Question: How do I add Win XP to Grub boot list?

---

### Post by Celauran on 2009-07-04
You'll need to edit your /boot/grub/menu.lst (I'd recommend backing it up first, just in case) and add the following:

```
title           Windows XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1
```

You may need to modify (hd0,0) depending on where XP is installed.

---

### Post by Don1500 on 2009-07-04
1. Post the output of:
```
gedit /boot/grub/menu.lst
```

2. What partitions are your OS's (Ubuntu & WinXP) located in?

---

### Post by louieb on 2009-07-04
> **SpinningAround said:**
> ...I did the mistake using setup (hd0,0) 
if XP is in the 1st partition that setup command made it un-bootable. 

Need the XP CD - boot to recovery console. and

```
fixboot c:
```after that the GRUB entry **Celauran **posted should work.

---

### Post by SpinningAround on 2009-07-09
Sorry for the late reply, I will give the output in menu.lst and fdisk -l since I think there is where the solution is.


> **Celauran said:**
> You'll need to edit your /boot/grub/menu.lst (I'd recommend backing it up first, just in case) and add the following:

```
title           Windows XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader     +1
```

You may need to modify (hd0,0) depending on where XP is installed.How do I know where XP is installed?

> **Don1500 said:**
> 1. Post the output of:
```
gedit /boot/grub/menu.lst
```

2. What partitions are your OS's (Ubuntu & WinXP) located in?I'm unsure exatly how I gain the information about where the partition is located but I'm posting both fdisk -l and menu.lst

**fdisk -l**
```
Disk /dev/sda: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc43bc43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3039    24410736   83  Linux
/dev/sda2            3040        3129      722925   82  Linux swap / Solaris
/dev/sda3   *        3130        3736     4875727+   7  HPFS/NTFS
```

**/boot/grub/menu.lst**
```

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=98360861-24be-4a31-9aed-c176fc9c9ae0 ro quiet splash
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=98360861-24be-4a31-9aed-c176fc9c9ae0 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.27-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=98360861-24be-4a31-9aed-c176fc9c9ae0 ro quiet splash
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=98360861-24be-4a31-9aed-c176fc9c9ae0 ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet
```


> **louieb said:**
> if XP is in the 1st partition that setup command made it un-bootable. 

Need the XP CD - boot to recovery console. and

```
fixboot c:
```after that the GRUB entry **Celauran **posted should work.I tested this since I understand how to do it, the xp mbr reset worked fine and I was able to boot into win but not into ubuntu (as it should be), but when I did restore grub was I no longer able to login to win XP and this isn't how it should work

---

### Post by boblemur on 2009-07-09
add:
```

title           Windows XP
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1
```


to grub (/boot/grub/menu.lst), and that should fix your problem :)

---

### Post by SpinningAround on 2009-07-09
> **boblemur said:**
> add:
```

title           Windows XP
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1
```


to grub (/boot/grub/menu.lst), and that should fix your problem :)

Thanks it worked :D Got two more question also ;) How do I make grub show the boot menu, since now I only get the "press ESC"?

Why does *update-grub* not find the partition with Win XP Pro SP3?

---

### Post by boblemur on 2009-07-09
1) you need to comment out the line. hidemenu its like the second paragraph

2) im not sure, linux isnt perfect, at least its better than windows in the fact that it has a boot loader that will even try and find other operating systems

---

