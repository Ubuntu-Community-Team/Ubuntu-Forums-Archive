---
title: "Missing hard disc"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by Peitx on 2011-03-28
Hi all!
I'm new to Ubuntu and I've some problems with my hard disc. Long story short, I buy a new computer with a 120GB revodrive (where ubuntu 10.10 32bits is) and two 2TB hard disc in RAID 1 configuration. The problem is that when I received it from the shop and I turn it on, I can't find my hard drives in Places!

Probably is not a mayor problem, but as I'm a newbie in Ubuntu I don't know how to fix it and I would like to save some data in the 2TB disks, not only buy it :)

I've read some post around Internet so I post here some info that I think would help to understand my problem (hope)

My fstab file:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/sil_acacdedfcgeb1 /               ext4    errors=remount-ro 0       1
/dev/mapper/sil_acacdedfcgeb5 none            swap    sw              0       0

I can see that there is an error but when (after google it) try to use fsck system say me:

/dev/mapper/sil_acacdedfcgeb1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

So I didn't continue process

I've no partitions so fdisk -l comand didn't show nothing

I've attached Disk Utility images because I think something is going wrong. In my laptop (were I also have ubuntu but without problems ) only appears my hard discs in Sata menu, but in this case appears so many disks in peripherical disks and my revodrive and Raid disks appears divided in two disks each. 

I don't know what to do to access my hard disks! Also I've the problem that I don't have Windows installed to check hard disk and Ubuntu is somewhat dificult for me, but I love it!

Can anyone know what is going on?

Thanks in advance!

P.D.: sorry for my basic english....

---

### Post by papibe on 2011-03-29
> **Peitx said:**
> ...
I've no partitions so fdisk -l comand didn't show nothing
...

You have to sudo it to show useful info:
```
$ sudo fdisk -l
```
Regards.

---

### Post by Peitx on 2011-03-29
Thanks for the comment papibe. If I use sudo fdisk -l I have the following answer:

Unable to seek on /dev/sda

That not sound great! Any idea about what is going on? probably if you have more info about my system you'll help better, so, please send me some commands and I'll post here the output

Thank in advance!

---

### Post by khelben1979 on 2011-03-30
It was difficult for me to see the small texts in the pictures, but it looks like you need to format the hard discs. There are tools from within Ubuntu so you can do this.

[GParted]("http://en.wikipedia.org/wiki/GParted") is a software you can use for this purpose, and you'll find it in the Ubuntu Software Center if it hasn't already been installed.

Being a newbie means it's wise to be careful and use the man pages to search for information when you feel uncertain. For instance you can type man gparted to see how it looks like. Take it slow is good also, not to rush things through, just creates more problems than you're asking for, in my opinion.

---

### Post by ronparent on 2011-03-30
Although dmraid, which is required to access raid drives, comes with the install image, it is not installed on your Ubuntu if the system is not installed on the raid. If you install dmraid you should be able to see and format the raid drive. If you format and partition the individual drives comprising the raid, the raid will be effectively broken.

---

### Post by Peitx on 2011-04-01
Thanks you for the answers guys

I'll start working with gparted and dmraid, using the man help and going slowly like khelben1979 suggest. I'll post any advance in order to help other newbies jeje

Thank you very much!

---

### Post by khelben1979 on 2011-04-04
You're welcome! 

Also in case you don't know much about RAID solutions, take a look here to read what [RAID 1]("http://en.wikipedia.org/wiki/Raid_1#RAID_1") is, in case you want to keep that configuration.

---

