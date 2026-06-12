---
title: "dumping windows after install"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by fishinsp on 2009-03-15
I have an old Dell laptop that I just installed the newest version of Ubuntu onto.  What is the easiest, safest method to removed Windows ME after the install.  I need the hard drive space.  Do I need to keep parts to boot up, things like that.  Never done this, and need basic answers.  Seem to keep finding too technical of answers and I am lost.

---

### Post by Yashiro on 2009-03-15
Install Gparted. (Gnome Partition Editor)
After install, run it and select the Windows ME partion.

Check out the right click menus.
Make sure the partition is unmounted. Reformat it to ext3 and give it a label.

---

### Post by bailbath on 2009-03-15
You could re-install Ubuntu but use the whole disk on the partition part of the installer that way everything will be configured correctly on your hard drive. Unless you need the space for a specific reason?
Ian

---

### Post by ajgreeny on 2009-03-15
If you have not too many files to backup from your new ubuntu, I suggest you do what bailbath says and reinstall using the whole disk.  If you just delete the windows partition, you will probably need to restore grub, which is easy enough, but it is also just as easy to start again, and at the partitioning stage of install, choose "Use entire disk" or whatever it's called.

---

### Post by lindsay7 on 2009-03-15
I agree, a new install would be easier than messing with the grub file after you repartition.  Take a look at Super Ubuntu on the web site. It could save you a lot of time setting up drivers and installing programs that you will end up installing anyway.

---

### Post by ugm6hr on 2009-03-15
If you have just installed Ubuntu, you do not need to keep anything.

Deleting Windows will not affect Grub at all.

Your choices:
1. Just reformat the Windows partition and keep it as a separate "data" partition.
2. Use the separate partition as /home [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
3. Re-install from scratch, using the "Guided - Use entire HD" option

---

### Post by egalvan on 2009-03-15
> **lindsay7 said:**
> I agree, a new install would be easier than **messing with the grub file after you repartition**.
  Take a look at Super Ubuntu on the web site. It could save you a lot of time setting up drivers and installing programs that you will end up installing anyway.

Since the MBR is not located on a partion, why should this be neccesary?

Only menu.lst need be changed, and this is rather easy.
In fact, it can be left alone, and only ubuntu chosen on boot.

---

### Post by lindsay7 on 2009-03-15
Live and learn. I thought that changing the partition size would at least require editing the grub menu file and or change the instructions because the partition numbers would have changed even it this was a one drive system. Would this also be true if the system had more that one drive.

I am not disagreeing with you, just trying to learn do and do nots of Ubuntu.

Thanks for the lesson.

---

### Post by fallingleaf on 2009-03-15
If you don't have any data you need on the Windows partition you could boot the Ubuntu live CD and try this:

* run the partition editor (under System-> Administration)

* delete the windows partition

* make a new partition in place of the windows partition, setting to to the smallest size possible and setting filesystem type to unformatted (this way you keep the same partition numbers and don't have to edit grub)

* resize the Ubuntu partition to fill up the rest of the space freed up by removing Windows

I hope that's not too technical :)

---

### Post by ugm6hr on 2009-03-15
> **lindsay7 said:**
> I thought that changing the partition size would at least require editing the grub menu file and or change the instructions because the partition numbers would have changed even it this was a one drive system. 

I was not proposing changing the partition sizes or order at all.  merely formatting the existing Windows partition.  It would still have the same identifier, but would now be blank.

---

### Post by Skol312000 on 2009-03-15
Ive been asking around the same question u are, iguess it all depends on if u want to save certain data... Im gonna try to delete all from live CD.  Pretty much Install Ubuntu again and let it overwrite over all drives

---

### Post by fishinsp on 2009-03-15
Thanks for the help.  I did not have enough RAM to use the live CD and had to use the text version.  Does thing change anything?

---

### Post by ugm6hr on 2009-03-15
> **fishinsp said:**
> Thanks for the help.  I did not have enough RAM to use the live CD and had to use the text version.  Does thing change anything?

No.

Only that the separate /home link I gave requires a LiveCD.

---

### Post by egalvan on 2009-03-15
> **lindsay7 said:**
> Live and learn. I thought that changing the partition size would at least require editing the grub menu file and or change the instructions because the partition numbers would have changed even it this was a one drive system. Would this also be true if the system had more that one drive.

I am not disagreeing with you, just trying to learn do and do nots of Ubuntu.

Thanks for the lesson.

Changing UUID's are one reason GRUB gets confused. GRUB uses UUID by default.

Deleting and re-making a partition WILL change the UUID.

Changing the SIZE does NOT alter the UUID, or the partition numbers.

Keeping the partitions in the same ORDER will NOT change the numbers.

Um, I don't know if RE-FORMATTING will change the UUID...

---

### Post by lindsay7 on 2009-03-15
I think I understan. By the way, I look at the sites in you signature line, what a great list of resources. Wish I would have found this a month ago.

---

### Post by monomanislive on 2009-03-15
hey i would just reinstall the whole os and wipe ME     BUT!!! SAVE all you important data (ie documents,,music ect.) to a jumpdrive it is so easy to get back your setting on ubuntu it will take you 2.5 hours tops to get everything back the way it was !!

---

### Post by theozzlives on 2009-03-15
> **fishinsp said:**
> I have an old Dell laptop that I just installed the newest version of Ubuntu onto.  What is the easiest, safest method to removed Windows ME after the install.  I need the hard drive space.  Do I need to keep parts to boot up, things like that.  Never done this, and need basic answers.  Seem to keep finding too technical of answers and I am lost.

ME?!!! ugh! Vista junior.

---

