---
title: "making ubuntu partition bigger"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by libihero on 2008-12-31
i shrunk my C drive again on vista, and i was trying to expand the drive that ubuntu was on, but it wouldn't let me, even though it would let me expand the shrunk C drive.  I have a blank space reserved for ubuntu, so what should i do now?

---

### Post by taurus on 2008-12-31
Did you try to expand Ubuntu using gparted?  Remember, you cannot resize Ubuntu while you are using it.  You have to use gparted either from the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Post the output of this command from a terminal to see where that free space is.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by libihero on 2008-12-31
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11f2341e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1441    11574801    7  HPFS/NTFS
/dev/sda2   *        1442       20932   156554376    7  HPFS/NTFS
/dev/sda3           24860       30401    44516115   83  Linux
malek@Maleks-Laptop:~$ 

that's what it says.  i want to make the linux one even bigger

---

### Post by linux_tech on 2008-12-31
unmount the Vista partition:

```

sudo umount /dev/sda1

```(I'm not sure which sda partition you want to resize)

Install GParted:

```

sudo apt-get update
sudo apt-get install gksu gparted ntfsprogs

```
Then start gparted
```

gksudo gparted

```
Resize the Vista partition, save changes

---

### Post by libihero on 2008-12-31
should i get rid of the empty space i made to make this work??

---

### Post by NightwishFan on 2008-12-31
Use the vista partitioner to shrink a vista partition. I believe you have to right click My Computer and hit manage, and it is somewhere in there. (Something like that I have used Ubuntu only for two years now. So my memory is like a lumber room, thing wanted always lost..)

---

### Post by Paqman on 2008-12-31
> **libihero said:**
> should i get rid of the empty space i made to make this work??

Not if it's in the right place, no. Just boot up into your LiveCD and go for it.

---

### Post by s3a on 2008-12-31
Use the Ubuntu live cd and NOT the harddrive installation like taurus said.

---

### Post by NightwishFan on 2008-12-31
Forget my post, it seems you did. Yes I agree use the live cd and grow it, no problem.. (Jeez im blind..)

---

### Post by libihero on 2008-12-31
OOO ok so i just use the live cd to grow the ubuntu?
how do i do that..?
choose manual... and then what?

---

### Post by Paqman on 2008-12-31
> **libihero said:**
> OOO ok so i just use the live cd to grow the ubuntu?
how do i do that..?
choose manual... and then what?

Nope, just boot up into the normal LiveCD desktop, then System > Admin > Partition Editor. You'll be able to make changes to your root partition, since it isn't mounted when you're running the LiveCD.

What *will* be mounted though is your swap partition. If that becomes a problem just right click and "swapoff".

---

### Post by NightwishFan on 2008-12-31
In live cd there is the gparted interface called "Partition Editor" in the Administration Menu. The interface is very user friendly, just right click the Ubuntu partition and hit resize. Should only take a few seconds unless you have to physically move the partition. In which case it may take a while.

---

### Post by linux_tech on 2008-12-31
this link explains with screenshots
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

