---
title: "Installing ubuntu on a existing, empty partition"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by takutosuki on 2009-12-06
Hello,
I am getting a new desktop computer tomorrow, and I am going to install unbuntu on a parition of my D drive. But since I have to look at a installig guide while installing ubuntu, and my laptop is currently broken, I will have to wait with installing ubuntu. So, my question is, can I format the D drive and make a partition that I will later use for Ubuntu, and then start putting my files on part of the D drive that won't be used for ubuntu (the partition)? 
without having to once again reformat the whole D drive again, I mean. i'll have files there soon. just the partition will be empty.

I'm sorry that I'm not good at explaining. I hope you understand.

---

### Post by The_Pirate_King on 2009-12-06
You can create a partition for Ubuntu from Window's "Disc Management" program.  When installing Ubuntu, you will have to select "Manual" when prompted to create a partition, and choose the partition that you created from Windows. 
Or, you could simply install windows and wait to create a partition when installing Ubuntu.  Ubuntu runs a very nice partitioning program at install called "GParted". 

In either case, you will not have to reformat your drive, and your windows files should remain intact. 
As long as you don't overwrite your windows boot partition with Linux Swap.  I made that mistake once...

---

### Post by ibuclaw on 2009-12-06
When you reach the partitioning bit of the Ubuntu installer - select "**Advanced**" and then select the second partition and set the partition as ext4 (or ext3 - your preference) and mountpoint as /

Regards
Iain

---

### Post by ranch hand on 2009-12-06
I assume you are installing from a LiveCD.

If this is the case, then do your partitioning from there.

Boot to the desktop, this is the first menu option on the CD, something like "try Ubuntu without any changes to your computer".

Go to System>Administration>Gparted (or it could be Partition Editor).

It should show all your drives.  Select the drive in the upper right hand corner.  Now you can see just what you have there and how much room.

You can only have 4 Primary partitions.  It would be best if you had 3 for Ubuntu but you could do it with 2.  The thing to do is partition the entire unused area of your drive as an "Extended" partition.

Extended partitions are a type of Primary partition that you can create many "Logical"  partitions in.

When you have done that just work inside that Extended partition and make a Swap partition at the very end of it (1Gb is plenty).  If you have more than 30Gb left then, starting at the beginning of the Extended partition, make a 10 to 15Gb ext4 partition for your / (root) partition.  Then make a partition ext4 for your /home partition 20Gb or bigger.  If you have more room you could make a 10Gb or bigger partition ext4 and put your files in there that you can later put in the /home partition.

Having a separate / partition gives you a better shot at reinstallling (if you reall screw your OS) as you can have the installer format that  partition and not format the /home partition.  Backing up is encouraged but I have never (yet) lost any data reinstalling this way.

When you install use the manual option in the installer/partitioner and and just edit the partitions you have already set up for / and /home so that they are used for those things.  The Swap partition should be detected with out interference on your part.

---

