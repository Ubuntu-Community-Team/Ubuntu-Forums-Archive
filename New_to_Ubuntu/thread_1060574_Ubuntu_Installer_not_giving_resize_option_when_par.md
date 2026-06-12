---
title: "Ubuntu Installer not giving resize option when partitioning"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Slaskie on 2009-02-04
Today, after a bit of research, I tried to install Ubuntu as a dual boot between 8.10 and Windows XP. I had spent the last week clearing space on my hard disk so I now have 75gigs of free space. When I began installing Ubuntu, everything went fine until I reached the partitioner. There were only three options:
>>Guided-use entire disk (Obviously since I was setting up a dual boot this was not the way to go)
>> Guided- use largest continuous free space (I was not planning to use this option, but just to try it out I selected it and got this message: **Failed to Partition the Selected Disc** This probably happened because the selected disk or free space is too small to be automatically partitioned.)
>> Manual: This was the option I was going to use all along. I was going to use the reccomended configuration for a dual-boot detailed at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) , but when I selected Manual and clicked next, the partitioner screen that came up did not have a resize option for the main 99gig partition. I tried Edit, but again there was no resize option. I am not sure if ubuntu is detecting my free space. Please help me with this problem :)

---

### Post by cartisdm on 2009-02-04
You didn't by chance hibernate your Windows before trying to install ubuntu did you?  That can cause problems with starting up the partitioner

---

### Post by Slaskie on 2009-02-04
Nope.

---

### Post by Slaskie on 2009-02-05
Bump :) I also tried gparted from the live cd to partition instead of the installer's partitioner so I actually had the resize option for my main 99gig drive. However, it did not let me shrink down my main partition, telling me that the minimum size of that partition was 101465Megabytes and the max size was 101473megabytes, a tiny difference. It seems ubuntu can't find my 75 megabytes o' free space?

---

### Post by Kawaiii on 2009-02-05
I'm having a similar problem!!
Dual booting Ubuntu from having XP installed.
I have 50 gigs of free space at the end of my hard drive. It's free space that I want to install ubuntu in. I'm installing from the live CD, and all the options that it gives me are wrong.
1) Guided 1 - This is the only option that keeps my two existing partitions in the "after" graphic. But it's resizing my partition to get the space- ignoring free space.
2) Guided 2 - No, I don't want to use the entire disk.
3) Guided Continuous Free Space - Uhm... The after graphic shows Ubuntu as using 100% of my hard drive now.  It's not free space, there's partitions I need to keep! I just want it at the end!
4) Manual - The after graphic shows "manual - 100% of drive". There are no options for it. Not very manual, I guess?

I will add that the "Before" picture shows the correct way my Hard Drive is- The two existing partitions and some free space at the end. But none of the after graphics seem to get it right.

Help? I figured I could just have it resize the partitions then afterward use gpardit to extend the partition to use the free space anyway. But this is just silly! How do I get it to use the free space that's there?

EDIT: some googling brought up few examples of people with similar problems, but no  helpful solutions. Link: [This problem]("http://en.kioskea.net/forum/affich-38577-ubuntu-installation-and-drive-partition") seems similar.

---

