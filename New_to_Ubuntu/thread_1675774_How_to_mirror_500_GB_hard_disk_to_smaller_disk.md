---
title: "How to mirror 500 GB hard disk to smaller disk?"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Fanatico on 2011-01-26
I have 500 GB hard disk with Ubuntu installing on it. It has boot (300 MB), swap(2 GB) and linux partitions. Let say linux partition is 300 GB, but actually in use is only 50 GB.

My question is how can I back up all these 3 partitions to the another hard drive which is smaller in size (let say 80 GB), so that I will have same Ubuntu system only on another smaller disk?

Particularly I need to know how to create image of Linux partition which contains only used 50 GB without empty 250 GB?

The bottom line is that I want to mirror 500 GB hard drive with Ubuntu (which actually use a bit more then 50 GB) to smaller hard drive of 80 GB.

Thanks

---

### Post by jfreak_ on 2011-01-26
I have a idea but its long winded and there IS a better solution out there. 
Shrink your hard disk to 50Gb, create a image and then re-expand it. Simple enough to say.

---

### Post by Grenage on 2011-01-26
Indeed.

Either create an identical partition table on the new drive, and copy the data over - or shrink and then mirror.  I'd personally copy the data, shrinking partitions is not risk free.

---

### Post by Fanatico on 2011-01-26
> **Grenage said:**
> Indeed.

Either create an identical partition table on the new drive

How can I create identical 300 GB partition table on 80 GB hard disk?

---

### Post by Fanatico on 2011-01-26
> **jfreak_ said:**
> I have a idea but its long winded and there IS a better solution out there. 
Shrink your hard disk to 50Gb, create a image and then re-expand it. Simple enough to say.

Could you provide more details, how can I shrink hard disk to 50 GB?

---

### Post by Grenage on 2011-01-26
> **Fanatico said:**
> How can I create identical 300 GB partition table on 80 GB hard disk?

Sorry, what I mean was, create the structure but vary the sizes.

---

### Post by Fanatico on 2011-01-26
> **Grenage said:**
> Sorry, what I mean was, create the structure but vary the sizes.

You mean recreate the same partition structure with help of GParted and then copy data something like this:

cp -aPR /dev/sda /dev/sdb

or

cp -aPR /dev/sda1 /dev/sdb1
cp -aPR /dev/sda2 /dev/sdb2
cp -aPR /dev/sda3 /dev/sdb3

But I still don't undersrtand how to copy sda3 (300 GB) to sdb3 (80 GB)?
Shrink sda3 to 80 GB or 50 GB ? How?

By the way can I find actual used space on unmounted volume?

Thanks

---

### Post by Grenage on 2011-01-26
Let's say you have this partition structure on disc A:

```
sda:
    sda1: 20GB
    sda2: 120GB
    sda3: 200GB
```

Now let's say you have about 10GB of data on sda1, 10GB of data on sda2, and 20GB of data on sda3.

You could create this data structure on a separate, smaller disc:

```
sdb:
    sdb1: 15GB
    sdb2: 15GB
    sdb3: 25GB
```

Then, if both are mounted, you could copy the data across from one partition to the other (these are obviously fictitious paths):

```
cp -Rp */mnt/partition_a1/* */mnt/partition_b1/*
```

You could use gparted to shrink the partitions, but there is _no guarantee_ that you won't lose data.  I've done it once, and it was fine; the data wasn't important.

---

### Post by kellemes on 2011-01-26
[Partimage]("http://www.partimage.org/Main_Page") will only copy used portion of your partition..

Edit: I see they don't support ext4??

---

### Post by Fanatico on 2011-01-26
Thanks for all your responses!

I however still can't mirror my disk:( My Linux partition is LVM partition, which is neither recognized by partimage, nor can be mounted as usual partition:(

---

### Post by JKyleOKC on 2011-01-26
Clonezilla might help:

From [http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla](http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla)

"So, if you have a partially used 10GB NTFS partition, you can squeeze it in a 4GB pen drive, and yet when restoring it on another disk, ask Clonezilla to create the original 10GB partition. Oh, and it can compress this data using gzip, bzip2, or lzo compression algorithms. In theory it should take a lot of time to compress the data, but on the chic dual-cores juiced with a couple of GB of RAM, you'd hardly have time to make coffee. I cloned an 80GB disk with one NTFS, one FAT, three ext3, and a Solaris ZFS partition on to a 40GB USB disk in under 20 mins. And it took less than half that time to restore."

I've not used it myself, but did find it interesting enough to dowload the live CD in case I need it in future...

---

### Post by bryanl on 2011-01-26
The thing is, you don't need to mirror the disk or any of its partitions.

All you need to do is to copy the files.

As noted in the earlier post, make target partitions big enough to hold the data on your existing source partitions then copy that data file by file using cp (or rsync or tar)

You will need to install grub on your new drive and you will need to adjust the UUID's in /etc/fstab so the proper partitions get mounted on the target drive when it boots.

The system you run to do these things should be separate from either the source or target drives - a live CD usually works well for this.

---

### Post by Splat_NJ on 2011-01-26
I haven't done it but IIRC [Remastersys]("http://geekconnection.org/remastersys/index.html") can do what the OP wants.

---

