---
title: "Triple Boot: XP, Win 7, Ubuntu 9.10 Grub2 Issues"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-11-21
Im triple booting these OS's on my MSI Wind. Now the problem is with XP, it is not recognized by Grub 2 instead the Win 7 bootloader takes care of it. In other words I have these options in the grub2 bootloader, Ubuntu and Win7 bootloader (which takes me to the Win 7 bootloader to choose either XP or Win 7). I would like to have XP as a option in the Grub2 bootloader along with Win 7 and Ubuntu. 

Heres the output of my ```
sudo fdisk -l
``` if i provides any help

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38b83a1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5874    47182873+   7  HPFS/NTFS
/dev/sda2            8429       13650    41945715    7  HPFS/NTFS
/dev/sda3            5875        8428    20515005    5  Extended
/dev/sda5            8307        8428      979965   82  Linux swap / Solaris
/dev/sda6            5875        8305    19526944+  83  Linux

Partition table entries are not in disk order

```

---

### Post by RookieUbuntuUser58 on 2009-11-21
Oh yeah and I would like to add, I saw that thread about changing the flag on XP from boot to none. But that doesn't seem to work unless your doing a install of Ubuntu after (which I can't do). I tried it from Gparted and it is still not recognized by Grub2.

---

### Post by wilee-nilee on 2009-11-21
For me it would help to have a screen shot of gparted looking at the partitions. This was addressed in a thread yesterday the answer that person found was having three separate partitions one for each OS. Now the real knowledgeable people may have a better explanation.

---

### Post by oldfred on 2009-11-21
You might be able to move the boot flag to the other windows and repair it. You probably will have to reinstall grub. Are both windows in primary partitions. If not then nothing will work.

Good info on Windows boot loaders
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)


Win7/Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by wilee-nilee on 2009-11-21
> **oldfred said:**
> You might be able to move the boot flag to the other windows and repair it. You probably will have to reinstall grub. Are both windows in primary partitions. If not then nothing will work.

Good info on Windows boot loaders
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)


Win7/Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

Thanks for stopping by I believe it was your help that got this similar problem fixed with another person yesterday. ;)

---

