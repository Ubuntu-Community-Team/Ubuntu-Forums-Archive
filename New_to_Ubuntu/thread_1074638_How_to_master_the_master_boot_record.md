---
title: "How to master the master boot record?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by kiruch on 2009-02-19
recently, i decided i should have Windows on my PC, too.
i created a primary NTFS partition after my Ubuntu partitions, found my disk images of a working copy of Windows, and copied them there.

but...
i had been stupid enough to let Ubuntu write its boot loader to /dev/hd0, and now programs like Boot Magic and Boot Manager refuse to install there.

i've tried *lilo*, but *liloconfig* tells me (translated):
> According to the configuration file /etc/fstab this program will use UUID=76c0118b-2346-41d7-988f-36773734f526 as a device for a root system. it doesn't look like a "usual" block device. Your fstab is wrong and you should correct it.
well, i dunno how :)

then i've tried *grub*, and executed *grub-install /dev/sda/*, but it didn't help me much: on boot, my PC just proceeds to Kubuntu splash screen.

i'm stuck and i hope someone will give me a hand.

---

### Post by LowSky on 2009-02-19
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

that should fix things for ya

---

### Post by caljohnsmith on 2009-02-19
It sounds like you just need to add an entry in your Grub's menu.lst to boot Windows. How about posting:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by kiruch on 2009-02-19
#*fdisk -lu*

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     6143759     3071848+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2        31824765    40017914     4096575    7  HPFS/NTFS
/dev/sda4         6143760    31814684    12835462+   5  Extended
/dev/sda5         6143823     6929999      393088+  82  Linux swap / Solaris
/dev/sda6         6930063    31814684    12442311   83  Linux 
```



#*cat /boot/grub/menu.lst*

```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=76c0118b-2346-41d7-988f-36773734f526 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=76c0118b-2346-41d7-988f-36773734f526 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet 
```



just a guess:
i feel like i should add to menu.lst something like
```
title         Windows
root          (hd0,1)
```
and maybe *chainloader +1*

---

### Post by caljohnsmith on 2009-02-19
> **kiruch said:**
> 
just a guess:
i feel like i should add to menu.lst something like
```
title         Windows 95/98/NT/2000
root          (hd0,1)
```
and maybe *chainloader +1*
Sounds good:
```
title         Windows 95/98/NT/2000
root          (hd0,1)
chainloader +1
```

---

