---
title: "Dual-Partition After Ubuntu Install"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by xnerdx on 2010-03-15
I hope I make this clear enough so that people can help me get my answer, I have a system setup that has Ubuntu 9.04 installed on my 300GB harddrive, I only have one harddrive connected to the computer. I am wondering if it is possible to modify the partition tables on my harddrive to create an NTFS for Windows without deleting the current linux partition? I have the linux partition using the entire harddrive but I have nearly 100GB of space I don't need. I'd like to remove about 50GB from the current linux partition and create a new partition without formatting my linux partition because the data on it is valuable. Also, if I achieved a dual-boot system with this harddrive can I make it so I can access the files on the linux partition from within the Windows OS?

Thanks everyone :popcorn:

---

### Post by J V on 2010-03-15
You can shrink the linux partition with a live cd, but windows has a tendancy to wipe everything you know and love weather you tell it to install somewhere else or not ;)

Suggest backup AT LEAST before trying this...

You can't let windows access linux if you are on ext4, so your only remaining option is to create symlinks so anything in your ~/Videos folder actually goes to /mnt/sda2/Users/YourName/Videos

---

### Post by xnerdx on 2010-03-15
It may have been a typo (Because I've never even heard of ext4) but I use ext3 lol but I think you mistyped that ^_^.
I have a plan to simply backup my entire system onto an external HDD and then format my 300GB HDD and setup several partitions for the linux systems and windows XP. Then I will just access what I need on the windows OS from the external HDD, I was just wondering if there was an easier solution.

---

