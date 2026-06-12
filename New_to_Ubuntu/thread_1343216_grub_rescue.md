---
title: "grub rescue"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by wobin77 on 2009-12-01
Hi,

Running Ubuntu for a few months now, never had any real problems until now. Was trying to create a bootlable usb for installing NBR to my asus1005ha (from which im posting now), but after rebooting my desktop, i suddenly get a grub error:

Grub loading
error : no such disk
grub rescue> _


I tried to format my usb device with gparted, but it hung up on me. So i killed the process with terminal. 

Now, grub wont load. Any help pls?


thanks in advance! 



ps: dualbooting vista-karmic on grub (not grub2)

---

### Post by ranch hand on 2009-12-01
Sounds strange to me.

However, it sounds like you need to straighten out grub-legacy.

First remove the USB device.

Boot into your LiveCD.  Open terminal and run;
```

sudo grub

```
This will give you a grub prompt like this   grub>
The following commands need run, in this order, at the grub prompts;
```

find /boot/grub/stage1

root (hdX,Y)

setup (hdX)

quit

```
Where X is your drive with grub stage1 and Y is the partition.  Both these numbers start counting from 0.  This, in your case should be easy as there should oly be one listing after the "find" command.  Just use it for root and drop the Y entry for setup.

---

### Post by wobin77 on 2009-12-01
thanks for your answer, but when i type fdisk-l i wont recognize my linux hard drive. I have two hard drives, one for vista, other for ubuntu.

i get:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8b4f367

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       41130   318082048    7  HPFS/NTFS
/dev/sda4           41130       60801   158009344    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partion table

```...posting this form gmail to gmail acc with live cd on desktop    :p



Edit:

well, seems my sdb has been erased for some odd reason... installing ubuntu again on sdb, see if i can boot again. 
Rly strange...

---

### Post by ranch hand on 2009-12-01
What happens if you pull up gparted?  System>Administration>Gparted (or maybe Partition Editor).

---

### Post by wobin77 on 2009-12-01
the same, i see my partions on sda (win bootloader, data and winre), but on sdb i see 'unknown'.
So, it seems my ubuntu disk has selfdestruct?  ;-) or the usb to disk app failed... 

well, reinstalled ubuntu 9.04 again and all s working again. Glad i had my files on a seperate hard drive   ;-)

---

### Post by isee on 2009-12-03
ranch hand your posts helped me.

Thanks !

---

