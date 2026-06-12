---
title: "Help with Partitioning an OS"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by fiveacez on 2009-05-05
I finally figured out how to dual-boot my computer with Ubuntu today!  Ubuntu is working great so far, but I've been trying to figure out how to partition my computer, and I need some help.

Here is what I want:
* A partition for Windows Vista Ultimate 64 bit (enough GB for the OS, NFTS)
* A partition for my programs and shared data (whatever is left over, FAT32)
* A partition for /home (5 GB, EXT3)
* A partition for the "/" partition (10 GB, EXT3) 
* A swap partition (6 GB)
* The partition for my HP Recovery Drive (10.9 GB, NFTS)

Right now, the partition that I want for my Windows OS has included in it program files, my user data and a few other things.  I want the Windows partition to have just the OS and have everything else moved to the data drive.  

What should I move to the other drive, and how would I do that? Do I just copy and paste from one drive to the other and then delete the copy in the OS drive, or is it a little more complicated than that?

Also, once everything is moved, how much space should I give for the Windows OS?

---

### Post by Marvin666 on 2009-05-06
Acronis Disk Director can create all of these partion types. If you look around enough you can find a "free" copy. Not for sure on the recovery one though, but my hard drive is set up like this:
1.465gb NTFS "TOSHIBA SYSTEM VOLUME" I have no clue as to what it is for, and left it untouched.
71.94gb NTFS Preinstalled Vista home
5.002gb Linux swap space
33.38gb EXT3 Xubuntu installation
To move your programs over, you have to uninstall them all, then reinstall, and under advanced select the letter of the partion, and folder you want it in.  Your swap space should be twice your RAM. During the ubuntu setup just select the partion you want to be home.

---

### Post by fiveacez on 2009-05-06
Well, I already made these partitions, but now I want to focus on isolating the window OS in its partition and move everything else to another drive.

---

### Post by Marvin666 on 2009-05-06
You have uninstall every program in the windows partion, then reinstall them all into their partion.

---

### Post by Didius Falco on 2009-05-06
You can move your "My Documents" folder to another drive, but I don't think there would be much point in moving all of the "program files" apps. In the case of a reinstall, you'd lose all the registry settings and have to reinstall them anyway.

You could move things like pictures, mp3s etc., that you make, and most, if not all, programs will let you set up where it goes.

But your best bet is to image the partition(s) so that you can just restore them if you run into problems. I make an image over every partition as soon as I get it all set up the way I want, and then start doing backups every month. A lot of people back up more, but all my own stuff is already back up in sevral places, so I'd just "lose" a few things I don't really *have* to have.

Ubuntu can read NTFS, so I'm curios why you'd want to use Fat 32 for that partition. It's really pretty much outdated these days, unless you have a specific need for it.

As to the size needed for Vista, you should check with Microsoft - I don't use it and never will.

Here is a PC World article about moving your Windows data to a separate partition.

[http://www.pcworld.com/article/159954/move_your_data_to_a_safer_separate_partition_part_1_xp.html](http://www.pcworld.com/article/159954/move_your_data_to_a_safer_separate_partition_part_1_xp.html)

I hope this helps...

Regards,

Didius

---

### Post by fiveacez on 2009-05-06
Thanks Didius. 
 
The reason I made the partition FAT32 was because [**this guide **]("http://www.psychocats.net/ubuntu/partitioning")used it, and it was the only one that I could find that gave me a decent explaination of what to do. (I would have asked here first, but I had a problem with my account to this forum.) I'll switch the partition to NTFS.
 
So now I know that the apps stay with the windows partition (another bit of information that I didn't know! I was under the impression that it was just for the OS. Someone should really make a dual-booting guide that goes through this partitioning stuff a lot better....).
 
The only question I now have is how much space should I give to fit in all of the apps that I'll be using. I have 200.7 GB to allocate, if that helps.

---

### Post by fiveacez on 2009-05-06
bump

---

