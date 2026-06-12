---
title: "Dual boot Vista Ubuntu - can't boot Vista anymore"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by jtait374 on 2009-02-05
I've been running a dual boot Vista and Ubuntu laptop for a couple of weeks. Unfortunately I've just updated Ubuntu and it has overwritten my menu.1st file. I now can't boot into Vista

I've spent an hour so far trying to work out what to add to my menu.1st file.

This is the result of sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    6  FAT16
/dev/sda2   *           6        1280    10240000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            1280       26365   201495117+   7  HPFS/NTFS
/dev/sda4           26366       30401    32419170    5  Extended
/dev/sda5           26366       30229    31037548+  83  Linux
/dev/sda6           30230       30401     1381558+  82  Linux swap / Solaris


Fortunately I have a backup of most of my Windows files, but my wife may not be pleased if I have to re-install (which I don't think I'll need to). 

latest menu.1st file


## ## End Default Options ##

#this just loads up the memory test service
#have tried (hd0.1) too...
title		Windows Vista
root		(hd0,0)
chainloader	+1
boot

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=cf2a9e8c-5c44-4657-bf21-31d7005f8c63 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=cf2a9e8c-5c44-4657-bf21-31d7005f8c63 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cf2a9e8c-5c44-4657-bf21-31d7005f8c63 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cf2a9e8c-5c44-4657-bf21-31d7005f8c63 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Any help gratefully received.
many thanks
James

---

### Post by caljohnsmith on 2009-02-05
OK, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then add the following entry after the last line in your menu.lst:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows Vista
root (hd0,1)
chainloader +1
```
Save, reboot, and let me know if that works OK or not. We can work from there if necessary.

---

### Post by jtait374 on 2009-02-05
Hi,
unfortunately it says 

Starting up ...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart

cheers
James

---

### Post by caljohnsmith on 2009-02-05
OK, I think I see the problem; even though your sda2 partition is marked as active or bootable, it looks like that is your Vista recovery partition based on its size. Your sda3 partition is probably your Vista partition, so how about instead trying:
```
title Windows Vista
root (hd0,2)
makeactive
chainloader +1
```
Let me know if that works or not.

---

### Post by jtait374 on 2009-02-05
many thanks; you're a star.

I had thought it was hda3 but couldn't work out that that equated to (hd0,2)

phew...

---

### Post by caljohnsmith on 2009-02-05
Glad to hear that worked OK; cheers and enjoy Ubuntu and Vista. :)

---

### Post by kansasnoob on 2009-02-05
caljohnsmith is a true star!

Totally an asset to our community!

---

