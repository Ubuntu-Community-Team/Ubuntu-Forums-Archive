---
title: "Help me with my Partitioning Nightmare"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by avianbc on 2009-10-22
Edit: this post has been solved. Please see my post at the bottom!

Please help me with my partitioning nightmare!

I attached an image of my current partition tables, which is a complete mess. To sum it up it looks like this (in order):

370 GB Partition with Windows Vista (C)
350 GB Unallocated Space
98 GB Windows 7 Partition (Z)
93 GB Ubuntu jaunty Partition
4 GB Swap
14 GB Unallocated Space

To be clear I want it to be:
500 GB Windows 7 partition
490 GB Ubuntu Jaunty + swap

I want to get rid of my Vista partition, but the thing is that it has about 200 GB of misc. files that I want to keep. I'd like to have just one partition at the start of the HDD (using about half the HDD space) for my Windows 7 installation, and another partition at the end of the HDD (using the other half of HDD space) for my ubuntu jaunty + swap.

Is it possible to move the windows 7 partition to the start of the drive while somehow keeping the 200GB of files from the Windows Vista partition?

I've tried using Partition Magic but it seems to error on x64 systems. Would Symantec Ghost be a better option? I've never really worked with ghost before so I dont know what I'm doing.

Thanks for reading my long post. :)

---

### Post by OrangeVixen on 2009-10-22
Do you have anything on your Ubuntu Linux partition that you want?

If not, then I would probably back up the files you want on the Windows partition on to a CD or something, maybe a second HDD would help, and then reinstall Vista and Ubuntu.

---

### Post by avianbc on 2009-10-23
> **OrangeVixen said:**
> Do you have anything on your Ubuntu Linux partition that you want?

If not, then I would probably back up the files you want on the Windows partition on to a CD or something, maybe a second HDD would help, and then reinstall Vista and Ubuntu.

I've spent a good number of hours customizing my Jaunty installation so I would like to avoid reinstalling it and starting from scratch. Only important files I have on it is my schoolwork + a ton of wallpapers in my home directory.

To be clear: I edited my original post. I want to keep only my Windows 7 partition and my Ubuntu jaunty + swap and if possible I'd like to keep my files from my old Vista partition.

---

### Post by X1R1 on 2009-10-23
You could use Clonezilla, a free open source back up and imaging software, VERY powerfull, just burn the ISO to a cd and run it from there. You can choose the files you want to back up and then restore them to a different partition. Or If you prefer something more use friendly, I recommend Acronis True Image. What you would do from whichever program you use would be:

-Back up your 200GB misc files.
-Delete/reformat the windows vista partition
-Go into your windows7 partition and increase its size to copy your 200 misc files there. If the software you are using allows you to merge partitions (that is, unite them) you could try to merge the win7 with the vista one. I know acronis supports partition merging, but I cant remember if clonezilla can do it, my guess is yes.

Also acronis supports moving partitions from one place to another so you could try that also.

Another workaround just came to my mind. Remember ubuntu can perfectly read/edit/create NTFS file system format, so you could INCREASE the jaunty partition size to fit your 200 misc files and get read immediately of that partition.

And for the love of god, dont ever EVER install vista again cause it sucks :lolflag:

hope it works and if you got any questions you can send me a PM if you want.

---

### Post by avianbc on 2009-10-23
Many thanks for your helpful post. Hopefully all goes well.

> And for the love of god, dont ever EVER install vista again cause it sucks 

Dont worry. I never installed it in the first place since it came with my new PC. Needless to say that I promptly installed ubuntu. :P

---

### Post by X1R1 on 2009-10-23
> **avianbc said:**
> Many thanks for your helpful post. Hopefully all goes well.



Dont worry. I never installed it in the first place since it came with my new PC. Needless to say that I promptly installed ubuntu. :P

Good to know :D :guitar::popcorn:

If you have trouble with acronis or clonezilla let me know and I will help you out in whatever I can.

---

### Post by mivo on 2009-10-23
Looking at this, I think the easiest, safest and fastest way is to backup the data you want to keep (may include setup/config files) and start from scratch. But that requires an external USB drive, and you didn't mention that you had one (they don't cost much, though). 

X1R1's approach may work. I would still hate to take the risk of losing the data without backing it up, if it is important data. Heck, even a 250 GB internal drive would do, and they are really inexpensive. :) But yeah, I'm one of those backup fanatics, I know!

---

### Post by undecim on 2009-10-23
If I were you, I would:

[LIST=1]
[*] Boot a LiveCD
[*]Back up your important files (an external HDD would be ideal)
[*]Press ALT+F2 and type "gparted'
[*]Use gparted to expand Win7 to consume the 350 GB unallocated space
[*]Copy your music to the Win7 partition
[*]Remove the vista partition
[*]Move and expand partitions to taste
[/LIST]
  Also, if you want to backup your Ubuntu install, (just in case you delete the wrong partition, your cat runs across your keyboard, or quantum mechanics cause a bit on your hard drive to flip,) you will need to copy your /home/ and /etc/ folders, and get a list of installed packages as explained at [http://ubuntuforums.org/archive/index.php/t-261366.html](http://ubuntuforums.org/archive/index.php/t-261366.html)

---

### Post by avianbc on 2009-10-23
Thanks for all the replies. For once Windows did something right and after I installed windows 7 over my old Vista partition it put all my old files in a folder called C:\Windows.old. I had already backed up all my data using acronis but ended up I didnt need to use it. Though it did eat my GRUB once again so I have to fix my bootloader again.

One last problem: I'd like to extend my linux partition to take up the remaining space on my drive. Last time I tried doing this, it stopped booting. Can someone walk me through it or point me in the right direction so I dont mess it up again?

I'll attach another image of my partition table. It is as follows (in this order):

820 GB Windows
94 GB Ubuntu Jaunty
4 GB Swap
13.5 GB Unallocated

As you should see I have 14 GB free at the end that I'd like to use on my Linux partition while moving my swap to the end of the drive.

> just in case you delete the wrong partition, your cat runs across your keyboard, or quantum mechanics cause a bit on your hard drive to flip
:lolflag:

Many thanks to all my fellow Ubuntu lovers. :)

---

### Post by X1R1 on 2009-10-23
> **avianbc said:**
> Though it did eat my GRUB once again so I have to fix my bootloader again.


Yeah that happens a lot. BUT!!! there is a neat and simple solution buddy. Super Grub Disk. it will AUTOMAGICALLY FIX all your boot problems in one click :D one of the best tools ever.

And to allocate the 13.5 GB you could just format that with whatever filesystem you are using in jaunty (ext3, reiserfs, ext2, etc).Or if you want more order use gparted or acronis to move the partition and then allocate (note: if you move your jaunty partition you will have to rerun super grub disk to fix your boot.

Here is the link for SGD: [http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml]("http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml")

I wanted to post the homepage but it is on maintenance or something cause I get a connection problem.

---

### Post by avianbc on 2009-10-23
Super Grub Disk is awesome. Thanks for the recommendation.

I ended up booting from liveCD to used gparted to extend the size of my ext3 jaunty partition to cover the extra space and moved my swap to the end of the drive. I figured I may as well go ahead and restore grub the old fashioned way through the command line since I already had the liveCD booted.

Thanks to you, X1R1, everything is finally in order and working beautifully. Many thanks for the help. :)

---

