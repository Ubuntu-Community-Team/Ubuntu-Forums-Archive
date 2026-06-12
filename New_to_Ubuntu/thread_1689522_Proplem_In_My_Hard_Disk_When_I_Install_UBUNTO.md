---
title: "Proplem In My Hard Disk When I Install UBUNTO"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by __.RaMy.__ on 2011-02-16
[CENTER][SIZE=3][COLOR=Blue]Hello...

i have Problem in my hard disk  when i try to Install UBUNTO..

That its show to me that i dont have any Drivers ... and i just have one and the size is 640 Giga ...

and when i make this (sudi fdisk -l)
he show to me this

[IMG]http://i53.tinypic.com/23gz2ox.jpg[/IMG]


and Gparted show that Hard Disk Is Unallocated 

[IMG]http://i55.tinypic.com/zkj1uq.jpg[/IMG]



and the Disk Utility Show like this 

[IMG]http://i52.tinypic.com/211mpk.jpg[/IMG]

I dont know why this it make with me
i'm using UBUNTO 10.10 x64



[/COLOR][/SIZE][/CENTER]

---

### Post by Aoude on 2011-02-16
Hi I see you're new to Ubuntu (as am I) it looks like you have a lot of unallocated space, this is empty space not being used by any of your partitions. If you install a program called gparted you should be able to extend your Ubuntu partition to the unallocated space. The problem may have occurred if you did not specify the partitions correctly during installation.

Install gparted through terminal by using the command

```
 sudo apt-get install gparted
```Hope this works for you. ;)

---

### Post by outleradam on 2011-02-16
When using Disk utility, select each partition and then click "Mount" from the options below.

You cannot mount SWAP partitions.

You cannot mount FREE partitions.

You can mount the partitions which are marked NTFS and EXT3.  

Your EXT3 partition would be better served as EXT4.   The NTFS partitons would be safer and more transportable as FAT partitons.

You may consider using your home dir and subfolders instead of separate partitions.  Using separate partitions for commonly accessed files s annoying and ugly in Ubuntu.  It may be in your best interest to just use your home folder and make subdirectories.   That's what your  home folder is for.

You may want to consider reformatting with a 500meg swap, 40 gig EXT4 for ubuntu and leave the rest for your videos and what not.

---

