---
title: "Help with dual booting Ubuntu and Hackintosh OSx"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by Kedster on 2010-01-03
I really would love to have OSX and ubuntu, I have played with this for hours, looked at endless amounts of forums guides and everything else.

fdisk -l
```
ketterer@ketterer-netbooky:~$ sudo fdisk -l
[sudo] password for ketterer: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19458   156290903+  ee  GPT
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

```
fdisk -lu
```
ketterer@ketterer-netbooky:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   312581807   156290903+  ee  GPT
/dev/sda4   *           0           0           0    0  Empty
Partition 4 does not end on cylinder boundary.
```


I am running grub2 now and have OSX 10.5.4 on the second partition.ubuntu is on the forth(with boot and grub on this partition) and then 3rd is a shared HFS+ partition that will be the home for ubuntu. and then the fifth is a swap partition. 

when I was using grub legacy I manually put OSX on the menu.lst 
```
title    OSX Leopard
root      (hd0,1)
chainloader +1
```

and I would get and error
```
starting up......
H000000000
HFS+ partition error
```

---

### Post by Crafty Kisses on 2010-01-03
Let's see your partition table first. So you can run the following commands in the terminal:
```
sudo fdisk -l
sudo fdisk -lu
```
Then I or somebody else can point you in the right direction.

---

### Post by Kedster on 2010-01-03
I posted the output to the commands above in the original post. I can only see 2 of what  I think 5 partitions. Im pretty sure sda1 is osx and sda4 is ubuntu

---

### Post by Kedster on 2010-01-03
I am willing to install grub lagacy again if needed(if u can tell me how) and i am able to load osx if u use the install cd so if i need to do anything over there it is possible

---

