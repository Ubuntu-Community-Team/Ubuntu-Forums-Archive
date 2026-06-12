---
title: "install Ubuntu manuall(without wubi) dual boot"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by sachin1992sharma on 2011-04-25
thanks all in advance
Okay coming to point
I need to install to Ubuntu manually without Wubi(for learning purposes):popcorn:.
But while installing Ubuntu I am stuck at partitioning while still trying to maintain dual boot with windows.
But :(i have one condition also I dont want to resize my partition, i have left 14 gb partiton drive for ubuntu.
Once again thanks:P

---

### Post by TeoBigusGeekus on 2011-04-25
Choose "Specify partitions manually".
Once in the partitioner, create the following 3 partitions out of your 14gb:
1)Swap partition; 1gb; to be used as swap (dah)

2)Root partition; 4gb; file system:ext4; mount point:/
That's where your system will be actually installed.

3)Home partition; 9gb; file system:ext4; mount point:/home
That's where your user settings will be stored - very useful in case of a reinstallation.

---

### Post by Zimmer on 2011-04-25
> **TeoBigusGeekus said:**
> Choose "Specify partitions manually".
Once in the partitioner, create the following 3 partitions out of your 14gb:
1)Swap partition; 1gb; to be used as swap (dah)

2)Root partition; 4gb; file system:ext4; mount point:/
That's where your system will be actually installed.

3)Home partition; 9gb; file system:ext4; mount point:/home
That's where your user settings will be stored - very useful in case of a reinstallation.

A bit too tricky without explanation of Logical partitions within a n extended one.

Yes, you will need to manually install to the 14gb partition you have there. Is it  already a partition? or just unallocated space?

How many Primary partitions do you already have ?

read some here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

