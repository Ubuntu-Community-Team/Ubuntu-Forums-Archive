---
title: "how do i format my hard drive to nfts"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Malik on 2009-09-03
i wanted to fresh install windows 7 but it said it cant cause it wasnt nfts i think. How do i reformat it to nfts on ubuntu?

---

### Post by pedja_portugalac on 2009-09-03
> **Malik said:**
> i wanted to fresh install windows 7 but it said it cant cause it wasnt nfts i think. How do i reformat it to nfts on ubuntu?

Malik Malik na govno si mi nalik.

---

### Post by drs305 on 2009-09-03
Use gparted: System, Administration, Partition Editor.

Highlight an existing primary partition or make one. (A primary partition must be one of the first 3 on the left if you also have an extended partition.) It should not be mounted.

Partition, Format, NTFS.

If NTFS is not displayed, check View, Filesystem Support to see if NTFS is supported by your version of gparted.  If it isn't:
```

sudo apt-get install ntfsprogs

```
Then restart gparted. You should now have NTFS support.

---

### Post by Malik on 2009-09-03
> **drs305 said:**
> 
Highlight an existing primary partition or make one. (A primary partition must be one of the first 3 on the left if you also have an extended partition.) It should not be mounted.


can u tell me what you mean here? what is the 3 things on the left? and how do i make a new partition?

---

### Post by drs305 on 2009-09-03
> **Malik said:**
> can u tell me what you mean here? what is the 3 things on the left? and how do i make a new partition?

Windows requires a primary partition. 

When you look at gparted, it shows all the partitions, in order. The first one on the left is the first partition, the second to the left is the second, etc.

To make a *new* partition, you must have some free/unallocated space. 

Perhaps it would be best if you provide us with a snapshot of your gparted screenshot. Then we can tell you how to proceed.

Here is the wiki link to partitioning:
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

Here is a screenshot of one of my drives. You will see two primary partitions, plus two logical partitions within an extended partition.

---

### Post by Malik on 2009-09-03
> **drs305 said:**
> Windows requires a primary partition. 

When you look at gparted, it shows all the partitions, in order. The first one on the left is the first partition, the second to the left is the second, etc.

To make a *new* partition, you must have some free/unallocated space. 

Perhaps it would be best if you provide us with a snapshot of your gparted screenshot. Then we can tell you how to proceed.

Here is the wiki link to partitioning:
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

Here is a screenshot of one of my drives. You will see two primary partitions, plus two logical partitions within an extended partition.
i just got one whole bar

[http://i28.tinypic.com/i21x68.png](http://i28.tinypic.com/i21x68.png)

I want to format the whole thing to ntfs so i can install windows 7.

---

### Post by k33bz on 2009-09-03
> **Malik said:**
> i just got one whole bar

[http://i28.tinypic.com/i21x68.png](http://i28.tinypic.com/i21x68.png)

I want to format the whole thing to ntfs so i can install windows 7.

if you want to reformat the whole drive then use a 98 boot up disk and go into fdisk.

---

### Post by drs305 on 2009-09-03
The partition must be unmounted. It looks like you are running Ubuntu. To unmount the partition, you must do it from a LiveCD or other 'rescue' CD. You can't do it while running a normal Ubuntu system. This would still leave you with pieces of Ubuntu. 

I would suggest performing this from Windows if you want to completely remove Ubuntu. Otherwise:


CAUTION: All data on sda1 will be permanently deleted.

Once you have booted from a LiveCD:

Select the first partition - sda1.
From the top partition, select Partition > Unmount.
Next: Partition, Format to, NTFS. Clcik the green check icon in the top panel.

---

