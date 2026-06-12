---
title: "how to add unalocated space to uduntu"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by spectron3 on 2011-01-26
i have 95gb of unallocated space and it is besides my home and i want to merge that space to get more home space. i tried using ubuntu livecd with gparted but its not showing anf free space besides my home so that i can expand it 
i attached a screen shot to make it more clear
all i want to do is to expand the /dev/sda1 all over unallocated space. 
i also added an attachment which shows what it is showing when i try resizing
please help

---

### Post by sikander3786 on 2011-01-26
Welcome to the forums :-)

sda5 seems to be your /home partition. And you've got Linux Swap partition in between the /home and unallocated space. So, if you want to merge it to /home you'l need to delete Swap partition, add the space to sda5 and recreate Swap partition. And you'll need to edit swap entry is /etc/fstab.

Instead, it would be lot easier to create a data partition in the free space and use it for storing your personal files.

Edit: sda1 seems to be the /home partition. My bad...

But the unallocated space is inside an extended partition. While sda1 is a primary one...

---

### Post by migs73 on 2011-01-26
> **sikander3786 said:**
> Welcome to the forums :-)

sda5 seems to be your /home partition. And you've got Linux Swap partition in between the /home and unallocated space. So, if you want to merge it to /home you'l need to delete Swap partition, add the space to sda5 and recreate Swap partition. And you'll need to edit swap entry is /etc/fstab.

Instead, it would be lot easier to create a data partition in the free space and use it for storing your personal files.

Surely sda1 is their Linux partition containing home?
Sda5 is NTFS, which I would assume is a windows partition.

Is the problem not that the unallocated space is actually inside an extended partition (sda2) so therefore cannot be added to sda1.

I would think (OP DON'T DO THIS I am not an expert on these matters) that they would require to resize sda2, to only have the swap and NTFS partitions in it, then the unallocated space should be available for sda1. 

I am a bit of a noob when it comes to partitioning, so this is mostly a question for the more experienced people out there.

---

### Post by Quackers on 2011-01-26
Your partition setup is a little odd, I would say.
From the screenshot it appears that you want to extend /dev/sda1 (the ext4 partition) is that correct? 
What is in /dev/sda5 (your ntfs partition)?

---

### Post by coffeecat on 2011-01-26
@spectron, in your screenshots you have either a 'save screenshot' or move/resize partition window covering much of the important information. Please post another screenshot without those obscuring windows so that we can see exactly what is going on.

---

