---
title: "GRUB Ubuntu + Debian (+ windows)"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Bölvaður on 2009-10-31
I installed Debian on a partition today (seen in bold at bottom of this post) 

My current boot partition is about 90mb partition at front of the second hard disk, set up by Ubuntu.

the debian kernels are not put into grub.lst after [FONT="Courier New"]$ sudo update-grub[/FONT]

moving from grub to grub2 and back to grub2 obviously has no effects either.

I should be able to boot into debian by the correct commands in grub. But it always says there is no partition by the name of (cannot remember... this (hd1,4) might be an example) or it complains about it doesnt find the files (Im guessing the kernel).

I've tried uuid but it was to wail. 


on my /boot partition (hd1,1) I think
```
## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		b7f1345c-f4c4-4ec4-bed0-aed78ec96f45
kernel		/vmlinuz-2.6.31-14-generic root=UUID=b2a5d927-ec03-43ab-8575-03705b020450 ro quiet splash 
initrd		/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		b7f1345c-f4c4-4ec4-bed0-aed78ec96f45
kernel		/vmlinuz-2.6.31-14-generic root=UUID=b2a5d927-ec03-43ab-8575-03705b020450 ro  single
initrd		/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-4-generic
uuid		b7f1345c-f4c4-4ec4-bed0-aed78ec96f45
kernel		/vmlinuz-2.6.28-4-generic root=UUID=b2a5d927-ec03-43ab-8575-03705b020450 ro quiet splash 
initrd		/initrd.img-2.6.28-4-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-4-generic (recovery mode)
uuid		b7f1345c-f4c4-4ec4-bed0-aed78ec96f45
kernel		/vmlinuz-2.6.28-4-generic root=UUID=b2a5d927-ec03-43ab-8575-03705b020450 ro  single
initrd		/initrd.img-2.6.28-4-generic

title		Ubuntu 9.10, memtest86+
uuid		b7f1345c-f4c4-4ec4-bed0-aed78ec96f45
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


### This isnt working, but it looks alright to me
### It was made by me.... it doens thave super cow powers :(

title		------ Debian ------
root


title		Debian
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.26-2-amd64 root=/dev/sdb7 ro quiet splash 
initrd		/boot/initrd.img-2.6.26-2-amd64
```


I did not install grub on debian as you can see, but I got all what is needed to add to my /boot partition I would have thought
```
$ ls /media/debian/boot
config-2.6.26-2-amd64          System.map-2.6.26-2-amd64
initrd.img-2.6.26-2-amd64      vmlinuz-2.6.26-2-amd64
initrd.img-2.6.26-2-amd64.bak

```


```
$ sudo fdisk -l
[sudo] password for gummi: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a75a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6080    48837568+   7  HPFS/NTFS
/dev/sda2            6081        6340     2088450   82  Linux swap / Solaris
/dev/sda3            6341       60801   437457982+  83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b779c4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8391    67400676    5  Extended
/dev/sdb2            8392       30401   176795325   83  Linux
/dev/sdb5               1          12       96327   83  Linux
/dev/sdb6              13        3866    30957223+  83  Linux
**/dev/sdb7            3867        6509    21229866   83  Linux**
/dev/sdb8            6510        8391    15117133+  83  Linux

```

---

### Post by louieb on 2009-10-31
Lots of ways to get Ubuntu to boot Debian. Most of what I know was learned here [IDBS GRUB Page]("http://members.iinet.net.au/%7Eherman546/p15.html")

Did not get enough information to make an entry for you. Please follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by Bölvaður on 2009-10-31
thank you very much.

I hope you'll see what Im missing



*added*
ok I can boot into debian now. But (probably) becaues I dont have the nvidia driver installed I just get a blank screen ^^
I pulled the information from the grub2 file grub.cfg which for some reason wasnt being used :S switched back to grub and added this to the menu.lst

```
title		Debian, kernel 2.6.26-2-amd64
uuid		b7f1345c-f4c4-4ec4-bed0-aed78ec96f45
kernel		/vmlinuz-2.6.26-2-amd64 root=UUID=c3fcfb48-b67c-406a-8e23-f0f277e814c6 ro quiet splash
initrd		/initrd.img-2.6.26-2-amd64
quiet

title		Debian , kernel 2.6.26-2-amd64 (recovery mode)
uuid		b7f1345c-f4c4-4ec4-bed0-aed78ec96f45
kernel		/vmlinuz-2.6.26-2-amd64 root=UUID=c3fcfb48-b67c-406a-8e23-f0f277e814c6 ro single
initrd		/initrd.img-2.6.26-2-amd64

```

---

### Post by louieb on 2009-11-01
Unless you have a separate /boot partition the both UUIDs should be the same.  The 1st UUID is the uuid if the partition with /boot. The one on the kernel line is  the Debian / (root) partition. 
```
title        Debian, kernel 2.6.26-2-amd64
uuid       [COLOR=Red] b7f1345c-f4c4-4ec4-bed0-aed78ec96f45[/COLOR]
kernel        /vmlinuz-2.6.26-2-amd64 root=UUID=[COLOR=Red]c3fcfb48-b67c-406a-8e23-f0f277e814c6[/COLOR] ro quiet splash
initrd        /initrd.img-2.6.26-2-amd64
quiet

title        Debian , kernel 2.6.26-2-amd64 (recovery mode)
uuid       [COLOR=Red] b7f1345c-f4c4-4ec4-bed0-aed78ec96f45[/COLOR]
kernel        /vmlinuz-2.6.26-2-amd64 root=UUID=[COLOR=Red]c3fcfb48-b67c-406a-8e23-f0f277e814c6[/COLOR] ro single
initrd        /initrd.img-2.6.26-2-amd64

```

I would still like to have the output of the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") (see post #2).

---

