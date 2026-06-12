---
title: "Grub wont boot windows"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2009-04-19
Ok, so I was reinstalling windows for a family member who managed to utterly destroy the registry =\ He didn't want me to take the computer home, so backing up the data was difficult, so I opted to install windows xp without formatting the drive, the default install path was c:\Windows2 at this point.

Ok, booted fine, I got all the drivers restored manually from C:\Windows and what not, no problem. Now I go to recover grub, did so as I always have by booting a live disk and doing the setup. Grub loads now, but wont let me into windows, I'm thinking it is because of the change between C:\Windows and C:\Windows2     =/

I would imagine this to be a simple enough solution, but for the life of me I can't find it. Any help?

EDIT::

By the way, here is the relevant context to my menu.lst file

> ## ## End Default Options ##
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		4befc327-2127-4170-a7dc-1a660a7fe738
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4befc327-2127-4170-a7dc-1a660a7fe738 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		4befc327-2127-4170-a7dc-1a660a7fe738
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4befc327-2127-4170-a7dc-1a660a7fe738 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		4befc327-2127-4170-a7dc-1a660a7fe738
kernel		/boot/memtest86+.bin
quiet


---

### Post by tjwoosta on 2009-04-19
please post the output of 

```
sudo fdisk -l
```

---

### Post by DoubleMcLovin on 2009-04-19
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38eedf0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6263    50307516   83  Linux
/dev/sda2            6264        6506     1951897+   5  Extended
/dev/sda3   *        6507       13053    52588777+   7  HPFS/NTFS
/dev/sda4           13054       30401   139347810    7  HPFS/NTFS
/dev/sda5            6264        6506     1951866   82  Linux swap / Solaris

```

---

### Post by tjwoosta on 2009-04-19
ok try changing this

```

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

```

make it look like this

```

title Microsoft Windows XP Professional
root (hd0,2)
savedefault
makeactive
chainloader +1

```


sda1 = hd0,0
sda2 = hd0,1
sda3 = hd0,2
and so on..

---

### Post by DoubleMcLovin on 2009-04-19
thanks ill try that now and get back to you in about 4-7minutes after boot.

---

