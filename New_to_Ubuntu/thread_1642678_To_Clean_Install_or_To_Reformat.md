---
title: "To Clean Install or To Reformat?"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by CrazzzyBudha on 2010-12-10
I have an Acer Aspire Timeline X. I am very new, so please excuse the ignorance on my part.

My laptop, of course came with Windows &, but no reinstall, or recovery disk. I made a partition for another linux distro, Peppermint, and dual booted with it. They each had about half the total hard drive space. Heres the dumb part; I wanted to switch to Ubuntu, but I read somewhere about the dangers of deleting a partition at the edge of the hard drive (where peppermint was) so I shrunk peppermint leaving a decent size chunk in the middle for Ubuntu. Here the even dumber part; when I was installing Ubuntu I didn't follow direction properly and ended up splitting my win7 partition in half again. End result:

Win7, Ubuntu, Swap, Big empty space, tiny peppermint, tiny swap. 

So now I'm trying to figure out an easy way to clean this all up. I need to keep win7, just in case I need it. I would consider doing a clean install of win7, then reloading Ubuntu, but I don't have a Win7 disk. 

Any suggestions or advice would be greatly appreciated.

---

### Post by zkriesse on 2010-12-10
First, welcome to the forums! Second, DON'T WORRY! There's probably a nice solution to all of this. Most new windows pc's come without a recovery disk by default BUT they have the necessary files for such a disk in a hidden folder on your pc which is accessible. [Windows 7 Recovery Disk]("http://www.ehow.com/how_5735259_create-windows-system-recovery-disc.html") should explain what I mean in detail for you. After you get that set up you can re-install Windows 7 and then make a partition for Ubuntu. That'd be my course of action but in truth it's a matter of opinion on what you'd like to run on your system. Hope this helps ya, but lemme know if it does/doesn't!

---

### Post by CrazzzyBudha on 2010-12-14
Hopefully this screenshot worked
[IMG]http://i1090.photobucket.com/albums/i372/Crazzzybudha/gparted.png[/IMG]

Thanks for the welcome and reply. If anyone has a second I would just like to check my plans here before I wreck my computer. In the pic, the first major partition, sda3, is my win7 partition. Next to that is my Ubuntu partition, sda9, followed by a swap, then a chunk of nothing currently formated to fat32, then a series of mistake partitions, the result of my learning experiences with linux in general. So, my plan is to leave the win7 and ubuntu partitions alone, and then delete everything else to the right so I have a big junk of unallocated space, and then resizing my ubuntu partition to fill it up. Does that make sense.

Also, I read somewhere that deleting a partition on the edge of the drive (Im worried about deleting the partitions to the right because of this) will make bad things happen. Is this something I should be worried about?

Thanks alot, I really appreciate all the help I get on these forums.

---

### Post by oldfred on 2010-12-15
I have not heard of any issues of deleting partitions to the right. Partitions do not have to be in order on the drive. I just do not like moving partitions left. 

You should leave about 30% free space in windows. But if you want to share data with Ubuntu and windows it is better to keep the windows system partition a little smaller and move data into a data partition. I do not like writing into a foreign system, reading is ok. So I only write into a windows system partition from Ubuntu if I have to do repairs.

Also for Ubuntu, it runs a little better if the system partition is 10-20GB. Then I have a separate /data (ext4 format) for all Ubuntu data. You can use /home for that but it has some user system settings data in hidden files and folders as well as your data files.

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)


The only swap you need to keep is the one mounted in fstab. If you are keeping your other Linux install you can change its fstab to use the same swap. Check UUIDs.

---

### Post by CrazzzyBudha on 2010-12-15
I'm happy to report all went well, I now have two nice sized partitions, one for Ubuntu and one for Win 7. I lost Grub somehow in the process, but had the foresight to create a live CD, search out a solution, and got it back. Now all is well. Thanks for the help and advice!

---

### Post by Jerry N on 2010-12-15
> **CrazzzyBudha said:**
> I'm happy to report all went well, I now have two nice sized partitions, one for Ubuntu and one for Win 7. I lost Grub somehow in the process, but had the foresight to create a live CD, search out a solution, and got it back. Now all is well. Thanks for the help and advice!

Congratulations!  You have taught yourself how to dual boot, how to partition, and how to restore grub.  You are now qualified as an **EXPERT** in these subjects and will now and forever be considered to be a **GURU** on these pages!

Jerry

---

### Post by zkriesse on 2010-12-15
Awesome...glad it worked...

---

