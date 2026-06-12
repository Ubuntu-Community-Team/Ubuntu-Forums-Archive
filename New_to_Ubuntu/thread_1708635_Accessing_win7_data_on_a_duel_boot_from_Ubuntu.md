---
title: "Accessing win7 data on a duel boot from Ubuntu"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by TempehtheLovely on 2011-03-16
I just installed Ubuntu onto a partition of my hard drive the other day. I am wondering if it is possible for me to access my files on the windows 7 partition from Ubuntu. I can get to the hard drive, but it doesn't seem to have any of my data. I'm mostly just trying to get my music and pictures, so it seems like this should be pretty straight forward. Could I partition my hard drive again to separate the win7 OS from all the media files? Or is there a better option?

---

### Post by hotrod6657 on 2011-03-16
> **TempehtheLovely said:**
> I just installed Ubuntu onto a partition of my hard drive the other day. I am wondering if it is possible for me to access my files on the windows 7 partition from Ubuntu. I can get to the hard drive, but it doesn't seem to have any of my data. I'm mostly just trying to get my music and pictures, so it seems like this should be pretty straight forward. Could I partition my hard drive again to separate the win7 OS from all the media files? Or is there a better option?

Your windows 7 files should be there.  Are you able to mount the partition that has your 7 install on it?

From there it should just be a matter of navigating to the right folders.

From that drive you should just need to open the "documents and settings folder" select all users, and there you should find your various Win 7 folders.

At least that is how mine works, yours may be slightly different depending on your setup, but it should be close.

---

### Post by TempehtheLovely on 2011-03-16
Ok, that is basically what I've gathered from google searches. I'm a tad confused about mounting the partition. I guess I just don't get how to do it, or what it means. Ha. Is that what I will have to do to access it? Thanks for the speedy reply!

---

### Post by hotrod6657 on 2011-03-16
if you go to the places menu at the top of the Ubuntu screen you should see, among other things, and entry called "computer."

If you select that you should get a window with the various partitions on your system.  One of them should have your windows install on it.  If it's like my system it will not have a identifying name by default.  Mine was called "196GB filesystem."  

If you double click them it should mount the partition and allow you to browse through the files on the partition.

This should also make the drive appear on your desktop.

Hope that helps, let us know.

---

### Post by TempehtheLovely on 2011-03-16
Right, ok. So that is what I have done. However, it seems to contain only random system files I can't open I can't seem to find any of the actual files I would see in Windows. Is this because Ubuntu can't read the formatting for the other partition? I'm betting this is something pretty dumb and trivial I just don't know about. Thanks for the help so far.

---

### Post by hotrod6657 on 2011-03-16
That shouldn't be the issue.

Your sure you're in the Windows partition?  I have a dual boot system and I can access the win 7 partition with no issue.

What are few names of the folders in the partition in question?

---

### Post by hotrod6657 on 2011-03-16
What is the name of the partition you're finding the odd files in?

---

### Post by TempehtheLovely on 2011-03-16
I'm thinking that might be the issue as well, because the partition I have mounted seems to be much MUCH smaller then the windows partition should be. 

Here is what I see in my computer: 
[IMG]http://i.imgur.com/5zUOp.png[/IMG]

I have been looking in the "640 GB Hard Drive: SYSTEM" folder, which is obviously wrong. None of the others contain any of the files I would normally see in my hard drive either. 

I have been able to sucessfully connect my external hard drive via USB, so its probably nothing dreadfully wrong.

I am looking for any of my windows files really. Seems like once I access the partition I will see them all. Program files, my music folder, videos, etc. Right now I have seen none of it.

---

### Post by hotrod6657 on 2011-03-16
What is on the 640 GB "Factory_Image" partition?

That seems like the next place I would look.

"Filesystem" should be your Ubuntu install.

Edit:

Have you tried booting to windows and verifying that your files are still there and accessible by Windows?

---

### Post by TempehtheLovely on 2011-03-16
Nah, the factory image is basically just a partition that came with the hard drive of a backup of the original system. I checked, and I never touch it on my windows system.

---

### Post by hotrod6657 on 2011-03-16
Have you tried booting in to windows and verifying that the files are still there?  That drive doesn't seem to be showing up in the file manager if it's still around...

---

### Post by TempehtheLovely on 2011-03-17
> **hotrod6657 said:**
> What is on the 640 GB "Factory_Image" partition?

That seems like the next place I would look.

"Filesystem" should be your Ubuntu install.

Edit:

Have you tried booting to windows and verifying that your files are still there and accessible by Windows?

Yes, I have been back on Windows and everything seems to be there and are accessible.

Here is the disk utility screen:
[IMG]http://i.imgur.com/HdjBH.png[/IMG]

It seems like it doesn't recognize that huge chunk that is my windows system (the 515 GB part). I checked for errors, seems to be in fine working order. Do I need to format it or something? That could mess things up though, and it seems like Windows has already formatted it.

---

### Post by hotrod6657 on 2011-03-17
I'm guessing that 515GB "unknown" portion is the part in question.

I'm at a bit of a loss.  I don't know what to suggest next.  Is your windows install encrypted?  

That's about the only thing I can think of that might keep Ubuntu from recognizing and reading the partition while Windows is able to do so.

Hopefully someone can provide more insight to your situation than I'm able to right now.

If I come up with something to try I will be sure to post.

Good luck, sorry I couldn't be more help.

---

### Post by TempehtheLovely on 2011-03-17
Ah, no problem. I'll check to see if it is encrypted or something. I think I have a more firm idea of the problem at this point though. Thanks for all the help. :) I bet somebody knows what is going on.....

---

### Post by Mark Phelps on 2011-03-17
Try opening a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one) -- and seeing what fdisk thinks of the partitions on your drive.  Please post the results back here.

---

### Post by TempehtheLovely on 2011-03-17
> Try opening a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one) -- and seeing what fdisk thinks of the partitions on your drive. Please post the results back here.

Yeah, so I just tried that. Here is what I got, and I'm not sure what it means. 

> Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848  1006480624   503136888+   7  HPFS/NTFS
/dev/sda3      1006481406  1225084927   109301761    5  Extended
/dev/sda4      1225084928  1250260991    12588032    7  HPFS/NTFS
/dev/sda5      1006481408  1216108543   104813568   83  Linux
/dev/sda6      1216110592  1225084927     4487168   82  Linux swap / Solaris


Again, not sure what this means. Seems ok? Could somebody decipher that?

---

### Post by Hero1969 on 2011-03-17
I think the clue is in the HPFS.  Look at this [[COLOR="Magenta"]page[/COLOR]]("http://www.linuxselfhelp.com/HOWTO/Filesystems-HOWTO-4.html").

---

### Post by TempehtheLovely on 2011-03-17
Would it be possible to give me a bit more info on that link? I'm pretty new to this, and most of the links on that page simply don't work.

---

### Post by Hero1969 on 2011-03-17
Actually let's look at something else, go back to the disk utility and click on the Unknows 515gb partition and let's look at at the screen.  While you're there, try to Unmount Volume and then Mount Volume.

---

### Post by TempehtheLovely on 2011-03-17
Here's a screenshot of the disk utility with the unknown portion selected.
[IMG]http://i.imgur.com/hppES.png[/IMG]
I checked this earlier. It won't allow me to mount or unmount the disk. I can reformat it or edit it.

---

### Post by Hero1969 on 2011-03-17
Sorry, this one is beyond me.  Something else, I would try out of curiosity is too boot from ubuntu live cd too see if you can see this partition from there.

---

