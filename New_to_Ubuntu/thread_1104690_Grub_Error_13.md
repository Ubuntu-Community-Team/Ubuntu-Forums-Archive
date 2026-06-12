---
title: "Grub Error 13"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Mortis03 on 2009-03-23
First off, I just wanted to say Hi to all and thanks for helping me already even though this is my first post, hehe.  

I just installed Ubuntu 8.10 onto my main desktop but have been using it on my laptop for a little bit now.  I was introduced to Linux when I had to play around with FreeBSD for a class, and I loved it so I decided to try Ubuntu out.  

Anyway, my set up is as follows:

3 Hard drives:
1 for pure storage - PATA
1 for windows partition / apps partition - SATA
1 for ubuntu - SATA

I set up ubuntu and I had a grub 17 error, but finally got that fixed.  Spent a lot of time here reading and boot using the live CD and edited the grub file.  

Normally, I would just spend a lot of time reading thru old threads and find a solution myself, but I'm kind of in a fix here.  I need my windows XP install to work on school stuff, so sorry about not using the search function.  

Anyway, any help would be greatly appreciated.  


Here is what I get when i use:  > sudo gedit /boot/grub/menu.lst

title		Ubuntu 8.10
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=710401da-4515-4ecb-b96e-c359d23e35a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=710401da-4515-4ecb-b96e-c359d23e35a3 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=710401da-4515-4ecb-b96e-c359d23e35a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=710401da-4515-4ecb-b96e-c359d23e35a3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP 
root		(hd0,0)
savedefault
makeactive

chainloader	+1

---

### Post by MaindotC on 2009-03-23
You may want to look into just running a VM of Windows on top of Ubuntu unless you're doing anything graphics-intensive like playing games.

I'm not sure which /dev your XP install is on.  Could you post the output of sudo fdisk -l?

---

### Post by Mortis03 on 2009-03-23
Well, I use a lot of Matlab, and spice utilities as well as the occasional games.  I plan on eventually only using linux, but I just don't have enough time right now to totally get rid of windows right now.   

Here is what you requested: 

> sudo fdisk -l


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef8def8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       60801   467901157+   7  HPFS/NTFS

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9f5e9f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4310    34620043+  83  Linux
/dev/sdb2            4311        4500     1526175    5  Extended
/dev/sdb5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07cd6ef8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS

---

### Post by MaindotC on 2009-03-23
Wine will probably be able to handle all your gaming needs, depending on your hardware and how well it is configured, and you can keep all of your windows stuff in a VM for things like MS Office.

Ok there are three NTFS partitions - sda1,2, and sdc1.  [Here's how you restore grub](http://www.sorgonet.com/linux/grubrestore/).  When it finds a root partition then it should adhere to the menu.lst you have set up because from what I see your entry for the XP install is correctly listed as (hd0,0).

---

### Post by presence1960 on 2009-03-23
> **Mortis03 said:**
> First off, I just wanted to say Hi to all and thanks for helping me already even though this is my first post, hehe.  

I just installed Ubuntu 8.10 onto my main desktop but have been using it on my laptop for a little bit now.  I was introduced to Linux when I had to play around with FreeBSD for a class, and I loved it so I decided to try Ubuntu out.  

Anyway, my set up is as follows:

3 Hard drives:
1 for pure storage - PATA
1 for windows partition / apps partition - SATA
1 for ubuntu - SATA

I set up ubuntu and I had a grub 17 error, but finally got that fixed.  Spent a lot of time here reading and boot using the live CD and edited the grub file.  

Normally, I would just spend a lot of time reading thru old threads and find a solution myself, but I'm kind of in a fix here.  I need my windows XP install to work on school stuff, so sorry about not using the search function.  

Anyway, any help would be greatly appreciated.  


Here is what I get when i use:  

title		Ubuntu 8.10
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=710401da-4515-4ecb-b96e-c359d23e35a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=710401da-4515-4ecb-b96e-c359d23e35a3 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=710401da-4515-4ecb-b96e-c359d23e35a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=710401da-4515-4ecb-b96e-c359d23e35a3 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		710401da-4515-4ecb-b96e-c359d23e35a3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP 
root		(hd0,0)
savedefault
makeactive

chainloader	+1

edit your windows entry in menu.lst to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP 
root		(hd0,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

you need the map lines in there.

Wine is very limited in what can be run successfully. You already have windows installed, that will run all software made for windows, wine will not. I say leave your dual boot intact unless you have no need for gaming or software that needs windows.

---

### Post by Mortis03 on 2009-03-24
> **presence1960 said:**
> edit your windows entry in menu.lst to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP 
root		(hd0,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

you need the map lines in there.

Wine is very limited in what can be run successfully. You already have windows installed, that will run all software made for windows, wine will not. I say leave your dual boot intact unless you have no need for gaming or software that needs windows.


Yeah, thats what I was thinking as far as dual booting windows.  

I tried that, but it didn't work.  I found that earlier when I was searching, but I must have taken it back out or something.

> **strAlan said:**
> Wine will probably be able to handle all your gaming needs, depending on your hardware and how well it is configured, and you can keep all of your windows stuff in a VM for things like MS Office.

Ok there are three NTFS partitions - sda1,2, and sdc1.  [Here's how you restore grub](http://www.sorgonet.com/linux/grubrestore/).  When it finds a root partition then it should adhere to the menu.lst you have set up because from what I see your entry for the XP install is correctly listed as (hd0,0).

My system specs are: 
Dual core CPU E2140 1.60GHz @ 2.4GHz
4gig ram - forget speed off top of head
8800gt
P35-DS3L mobo

One program I need to use right now is diptrace.  Happen to know if that works with wine, or has a linux version?  I'll check that out.

I'll try out what you suggested now


Thanks to both of you

---

### Post by meierfra. on 2009-03-24
Add this to the end of menu.lst

title		Microsoft Windows XP  (hd1)
rootnoverify    (hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

and

title		Microsoft Windows XP  (hd2)
rootnoverify    (hd2,0)
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


Reboot and  try both entries. If one of them works, deleted all the other Windows item from menu.lst. If none of them work, report all error messages you got.

---

### Post by Mortis03 on 2009-03-24
> **meierfra. said:**
> Add this to the end of menu.lst

title		Microsoft Windows XP  (hd1)
rootnoverify    (hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

and

title		Microsoft Windows XP  (hd2)
rootnoverify    (hd2,0)
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


Reboot and  try both entries. If one of them works, deleted all the other Windows item from menu.lst. If none of them work, report all error messages you got.


Will do.  As far as restoring the grub file... do I need to boot from the live CD to do that?  When I tried doing that not booting from the live cd, I was getting errors saying like device not found.  I'll get the quote of the error in a second.  

Also, does anyone know why ubuntu is listed twice on the boot selection?  When I was installing it, I ended up installing it a second time, but I thought I reformated again.  Do I have 2 ubuntu installs, or is it just listed twice in the grub file

Thanks

EDIT:

Ok, Well, I tried, and the first one worked.  Thank you very much for your help.  Now, I just got to figure out my dual monitors. 

Any info on my last question?

---

### Post by MaindotC on 2009-03-24
There are five entries for Ubuntu:  Two for the 2.6.27-11 kernel, and two for the 2.6.27-7 kernel.  Each kernel has a recovery mode boot option that brings you to a terminal instead of trying to boot into X.  This is useful if you have problems with X.  It's similar to booting from a livecd but you're running off of the hard drive and you can fsck or unmount the filesystem.  The last entry is a memory test to test your memory modules - useful if you're ever getting squashfs errors.

Do everyone a favour and put your hardware & a link to the manufacturer documentation in your signature like mine.  It'll help in the future if you have any other troubleshooting issues.  This particular issue wasn't relevant to that information but it's still helpful.

---

### Post by bell2jd on 2009-03-26
to the OP, how did you solve your GRUB error 17 problem? I'm having that issue, and I can't even boot from my live CD. Needless to say, I'm quite flummoxed by this. Thanks.

---

