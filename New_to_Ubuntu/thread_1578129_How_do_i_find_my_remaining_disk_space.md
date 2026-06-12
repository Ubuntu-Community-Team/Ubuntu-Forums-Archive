---
title: "How do i find my remaining disk space"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by juve_t on 2010-09-19
Hello all i am new to ubuntu and just installed ubuntu 10.4 on my laptop. i have a hard disk space of 250gb during the installation process i created two partitions. the first one was 152gb and the second 8gb for the swap partition. the remaining 90Gb was left unpartioned. After starting my system i could not find it anywhere, can any tell me how to find the 90gb

thanks in adavance

---

### Post by rockerphil on 2010-09-19
in my opinion the program baobab is a pretty good tool to analyze disk usage. it'll tell you exactly what is using disk space and where it's being used, and it'll even give you a nice little pie graph for visual aide. if you are using the standard Ubuntu install (using Gnome) then it should already be installed. simply press Alt+F2 and type in "baobab" without the quotations of course. if for some reason it isn't installed simply pull up a terminal and run this command.

```
sudo apt-get install gnome-utils
```

as to your second question about the 90 GB partition the reason you can't find it is because it isn't formatted, so you need to give it a file system, either a Linux native like ext2/3/4 or NTFS if you plan to use it as a shared partition on a dual boot with Windows. this can be done with Gparted, again, if you're using Gnome it should be installed, but if for some reason it isn't it can be installed with this command

```
sudo apt-get install gparted
```

just remember to be careful with gparted as it can be a potential weapon of mass destruction

hope this helps,

Phil

---

### Post by pclancy on 2010-09-19
There are a couple different ways to check this.  One way is to use fdisk.  Here's what it looks like when I run it:
```
$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f1c38f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14107   113314446   83  Linux
/dev/sda2           14108       14593     3903795   82  Linux swap / Solaris

```

If you'd like to modify the partitions, I'd recommend gparted.  That also gives you a nice graphical view of your partitioning.
```
$ sudo apt-get install gparted
$ sudo gparted

```

Hope that helps.

---

### Post by garvinrick4 on 2010-09-20
```
sudo parted -l
``` (lower case L)
Tells you size in megs or gigs

---

### Post by HermanAB on 2010-09-20
Another handy utility is Disk Free:
$ df

---

### Post by k33bz on 2010-09-20
```
df
```
or
```
df -h
```

---

### Post by juve_t on 2010-09-22
Thanks a lot. i installed gparted and was able to get the disk space

---

