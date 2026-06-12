---
title: "How to triple boot with ubuntu, win 7 and fedora 15 already installed ?"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by hunkgagan on 2011-06-06
Hi all ,

How can I install ubuntu over win 7 and F15 ? 

Thanks.

---

### Post by hunkgagan on 2011-06-06
anyone ??

---

### Post by jaacko on 2011-06-06
I understand your question so that you have Windows 7 and Fedora 15 currently installed and you want to install Ubuntu along these. That's what you want, right? :D

If so, just download an Ubuntu iso-file from the website and burn it to a disk. Then boot the PC from the newly burned disc. The Ubuntu installer can automatically take care of partitioning but you could free up some space on your hard drive for example in Fedora and then install Ubuntu on that free space.

The installer also automatically detects other installed operating systems and configures GRUB so that you can boot into all of them.

Hope this helped. I assume you have some experience in handling partitions and installing operating systems since you already managed to have Windows 7 and Fedora 15 play nicely with each other. :)

---

### Post by JohnBonne on 2011-06-06
This works so I could put mint on an external drive?

---

### Post by hunkgagan on 2011-06-06
> **jaacko said:**
> I understand your question so that you have Windows 7 and Fedora 15 currently installed and you want to install Ubuntu along these. That's what you want, right? :D

If so, just download an Ubuntu iso-file from the website and burn it to a disk. Then boot the PC from the newly burned disc. The Ubuntu installer can automatically take care of partitioning but you could free up some space on your hard drive for example in Fedora and then install Ubuntu on that free space.

The installer also automatically detects other installed operating systems and configures GRUB so that you can boot into all of them.

Hope this helped. I assume you have some experience in handling partitions and installing operating systems since you already managed to have Windows 7 and Fedora 15 play nicely with each other. :)

Thanks,

I have free(Unpartitioned) space on my hard disk. While I am trying to create an unformatted partition with windows for ubuntu installation, It is giving error for limit of number of partitions on the disk. Will ubuntu partitioner be able to handle this issue. I fear of loosing my previous installation and data . What should I do ?

---

### Post by Lateralis on 2011-06-06
Regarding the partition limit number, you can only have 4 *primary* partitions on a hard drive.  However, you can make one of these primary partitions an *extended* partition.  This extended partition is like a container, into which you can have as many *logical* partitions as you like.

---

### Post by jaacko on 2011-06-06
> **hunkgagan said:**
> Thanks,

I have free(Unpartitioned) space on my hard disk. While I am trying to create an unformatted partition with windows for ubuntu installation, It is giving error for limit of number of partitions on the disk. Will ubuntu partitioner be able to handle this issue. I fear of loosing my previous installation and data . What should I do ?

The error means exactly what it says. You can't have more primary partitions on your hard drive at the moment. This wikipedia link explains the issue pretty well: [http://en.wikipedia.org/wiki/Disk_partitioning#PC_partition_types]("http://en.wikipedia.org/wiki/Disk_partitioning#PC_partition_types").

This complicates things a bit. You either need to remove a primary partition and replace that with an extended partition, assuming you don't already have an extended partition on that hard drive. Or, you could modify your partitioning by moving the Fedora partitions into an extended partition. I believe Linux can boot from an extended partition (I know Windows needs a primary partition to boot from), also **correct me if I'm wrong with this**.

Or the easy way is to install Ubuntu on a completely different hard drive. This can be tricky if you have a laptop, though.

Edit: fact corrections...

---

### Post by raja.genupula on 2011-06-06
i am succeed with this
first make the partitions , for each OS how much size you wanna allocate. 
after that first go for windows 7 , then go for fedora , then Ubuntu
so when the system starts GRUB will show all the things and you can move from there

---

### Post by hunkgagan on 2011-06-07
according to windows partitioner it shows fedora's partition(4th primary partition) a primary partition. but another partition software software shows it as a logical partition. 

and can I change the type of fedora's partition from primary to logical, if it is primary. while fedora is running on it ?

---

