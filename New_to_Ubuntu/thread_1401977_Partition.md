---
title: "Partition"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by SirRedTooth on 2010-02-08
How can I uninstall ubuntu and move it over to a different partition.
I installed using a USB.

I don't have a windows installation CD, but my manufacturer has a 'hidden' partition which I cannot edit that contains factory settings + OS ( i think ).


[B]Basically whats the fastest easiet way to move ubuntu to a different partition?
(I didnt use wubi to install)
Note that I didnt install ubuntu in a different partition to windows. It runs alongside windows in the same partition.
[/B]

---

### Post by Tahakki on 2010-02-08
Probably with GParted. Note that messing with the Windows partition can easily corrupt it due to fragmentation. If you're moving windows partitions around, do it with the tool in windows itself.

---

### Post by 7raTEYdCql on 2010-02-08
Well i didn't really understand your question. Does it mean, that you've replaced windows with Ubuntu? Cause to my knowledge, you can't have two operating systems on the same partition.

---

### Post by audiomick on 2010-02-08
I also believe it is not possible to have 2 OSs in one partition.
You had best post the output of
```
sudo fdisk -l 
```here so that people can see your partition setup.

---

### Post by louieb on 2010-02-08
I use Gparted. [Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm")

---

### Post by SirRedTooth on 2010-02-09
Here is sudo fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9eb47d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1045     8393931   27  Unknown
/dev/sda2   *        1046       13903   103280640    7  HPFS/NTFS
/dev/sda3           13904       16544    21213832+   7  HPFS/NTFS
/dev/sda4           16545       19457    23398672+   5  Extended
/dev/sda5           16545       19331    22386546   83  Linux
/dev/sda6           19332       19457     1012063+  82  Linux swap / Solaris

```Note on the screenshot that the Ubuntu partition 22gig NFS is actually empty.

---

### Post by audiomick on 2010-02-09
Ok, so what do you have in mind to do?
What you have is your windows install in partition sda2, and your linux install in sda5. They are already in different partitions, as must be the case.
Could it be that you mean you want to put Ubuntu on a different hard drive?

---

### Post by Miljet on 2010-02-09
> Note that I didnt install ubuntu in a different partition to windows. It runs alongside windows in the same partition.

You did in fact install Ubuntu to a different partition than Windows. To be exact, you installed it to sda5. As others have said, you cannot install 2 different operating systems to a single partition unless you install one within the other such as wubi or a virtual system.

It appears that you have named sda3 as Ubuntu although it is formatted as NTFS, which is a Windows file system. And of course it is empty.

So what is it you want to do? Move Ubuntu from sda5 to sda3? I can't see that it would benefit anything. Why not just use sda3 as a shared data partition? But if you are determined to have Ubuntu on sda3, the easiest and fastest way will be to just re-install Ubuntu.

---

### Post by SirRedTooth on 2010-02-09
Oh sorry I didnt realise that ubuntu was already on a different partition.
Sorry about this :p I feel stupid and relieved that I can finally get back to studying and finish messing around with my OS.

So just to verify.
Ubutnu is already on a separate partition to windows?

---

### Post by Miljet on 2010-02-09
Yes, it appears that Ubuntu is installed on sda5.

---

