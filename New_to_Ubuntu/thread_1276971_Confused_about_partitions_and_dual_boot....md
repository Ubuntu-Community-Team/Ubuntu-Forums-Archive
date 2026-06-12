---
title: "Confused about partitions and dual boot..."
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Chewy2 on 2009-09-27
Alright so I'm new to Ubuntu and I am trying to have my computer dual boot with it and Vista.  I'm just really confused about what to set the partitions to(mostly because I don't exactly understand what they are). I have a 105gb HD, with 28GB free. I tried to shrink the Vista partition with the disk management thing that comes with it, but that only freed up 77mb. Not sure if this means that the Ubuntu install thing will still be able to shrink it or what.  

So what should I set my partition sizes to? I plan on using Ubuntu for just about everything except for things I can only get to work on Vista. Am I going to have to free up a lot more disk space or what?

---

### Post by TiredBird on 2009-09-27
No need to feel confused, partitions are really pretty simple.

Unless you have some unusual needs, 5GB is more than adequate for a full install of Ubuntu. (I have over five full installs and none is a partition that is greater than 5GB). Only about 3GB is for the system, the rest is for personal use. If you want more your own data, just increase the size - make it 10 GB, then you'll have about 7 GB for your stuff.

Ubuntu can read and write data to the windows partition quite easily but reading and writing ubuntu from windows is not so easy. So don't put any data on the Ubuntu partition that you're going to want in Windows.

Make another partition of 1GB for swap space. (Windows buries its swap space in the filesystem - Linux wants a separate partition.)

Actually thats all you need. If you have an Ubuntu install disk, boot from it and it will start up a partitioner for you to do the stuff above. When you're done, let it install Grub as the bootloader on your main drive. It'll even find Windows for you and add that to the menu.

---

### Post by yanceypd on 2009-09-27
Often see recomendations to defrag Windows before installing Ubuntu.  This helps compact space on drive that Windows occupies.  May prevent issues.

---

### Post by Chewy2 on 2009-09-27
Alright, so I can increase my Ubuntu partition and decrease my Vista partition at any time in Ubuntu? 


I've read some conflicting things about them though. Can I or can I not access the files on my HD on my Vista partition when using Ubuntu?

What I'm thinking about doing is just putting all of my files on an external HD and transferring them to Ubuntu as I need them, and deleting them from Vista once I got them to work on Ubuntu. Does this sound like a good plan?

---

### Post by TiredBird on 2009-09-27
I just reread your post and I think I now understand that your Windows system is actually taking up the whole hard drive. You used windows software and were able to free up 77 MB. You need more room. Do the following:

Unless you have a lot of music and/or video files, I can't fathom how you can be using so much space. Unless you know what all of it is, take a look through your files and get rid of the stuff you don't need. 

Then run a defragger on it get it organized reasonably.

Then boot with the ubuntu install disk. If I'm not mistaken, it will free up the space you need.

Then do what I suggested in the earlier post.

If you need more help, ask.

---

### Post by yanceypd on 2009-09-27
If you have a lot of music or photos burn them to CD or DVD's and they are safe.  Look on this forum for tip and how to's.  Im sure you can do some file swapping.  I'm just not familiar with that.  I use a fairly compact setup and tinker a lot so I burn all important stuff.

---

### Post by Chewy2 on 2009-09-27
My entire hard drive isn't being used, I have 28GB free. But it is still all being used in the Vista partition. So I have about 70 gigs of stuff on my computer, which does seem like a lot but I'm not one to delete things like random pictures and stuff. About 20 GB is the windows OS(everything in the Windows folder), then about 15 for games, and then a lot of music as well(maybe 10-15 gigs worth). My computer is very sloppily organized so its kind of tricky finding out what the hell the other stuff taking up room is(I know my desktop folder is 20 gigs).

So should I just clean up a bit and give Ubuntu about a 10-20gb partition and increase it when I need to?

Oh and I have an external HD with lots of free space so moving a lot of my files to that shouldn't be a problem.

---

### Post by TiredBird on 2009-09-27
> **Chewy2 said:**
> Alright, so I can increase my Ubuntu partition and decrease my Vista partition at any time in Ubuntu? 


I've read some conflicting things about them though. Can I or can I not access the files on my HD on my Vista partition when using Ubuntu?

What I'm thinking about doing is just putting all of my files on an external HD and transferring them to Ubuntu as I need them, and deleting them from Vista once I got them to work on Ubuntu. Does this sound like a good plan?

I wouldn't recommend that you plan and changing the sizes of the partitions on a regular basis. Software that does this doesn't always do what you expect. Set up 10 GB to start with on Ubuntu. Then as you want to add more data to Ubuntu, add additional partions.

I don't think I would go the external hard drive route either. You can access the Vista data from Ubuntu. As you gradually begin to use portions of the data only for Ubuntu, copy it into a Linux partion and delete it from Vista when you're satisfied that its safely on Linux. If you do that, every so often you can reduce the size of the Vista partition. 

It took me a couple of years for the ful migration from Windows but I now use Ubuntu exclusively. I have several computers and none of them run Windows anymore.

I have several external drives. They're great for backup but I don't like them for much else.

---

### Post by Chewy2 on 2009-09-27
Alright, well I'm gonna use a 20GB partition with a 2gb for swap space(since I have 2gb RAM I should do this, right?), and go from there.

Just after I back up all my stuff in case I mess something up...

---

### Post by Captain_tux on 2009-09-27
Be sure to defrag and run **chk dsk** from a Windows command prompt a couple of times before you start partitioning in order to reduce the chance of disk errors. Oh, and back up all your important files!

Good luck and welcome to the real world of computing!

Edit: Take a look at my first posts ([http://ubuntuforums.org/showthread.php?t=996303](http://ubuntuforums.org/showthread.php?t=996303))... I also had issues about partitioning.

---

### Post by oldfred on 2009-09-27
Understand that installing a new operating system is brain surgery. While it is designed to work and does in most cases errors can occur. Back up important data.
It is best to use Vista's partition tool but not mandatory any more:
Herman on Gparted old error and not in Ubuntu but still use Vista partitioner for safety:
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

I always like to make sure that if there is an issue I have a way to go back.  The liveCD is first, but I like to have Supergrub, and a live Gparted CD as well as any Windows CD to reinstall windows boot if necessary.

Starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.

Info on resizing:
Using GParted to Resize Your Windows Vista Partition 
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

If your PC did not come with a complete Vista installation CD, you can download a Vista Recovery Disc at the following link:
Windows Vista Recovery Disc [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) 

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Did I mention that you should backup important info first?:)

---

### Post by yanceypd on 2009-09-27
Everyone here will help if possible.  Advance prep is real important before trying a new OS.  Enjoy Ubuntu it really a trip to have control and a stable system.  Mistakes happen and we don't want you to get frustrated.

---

### Post by Chewy2 on 2009-09-27
> **oldfred said:**
> Understand that installing a new operating system is brain surgery. While it is designed to work and does in most cases errors can occur. Back up important data.
It is best to use Vista's partition tool but not mandatory any more:
Herman on Gparted old error and not in Ubuntu but still use Vista partitioner for safety:
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

I always like to make sure that if there is an issue I have a way to go back.  The liveCD is first, but I like to have Supergrub, and a live Gparted CD as well as any Windows CD to reinstall windows boot if necessary.

Starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.

Info on resizing:
Using GParted to Resize Your Windows Vista Partition 
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

If your PC did not come with a complete Vista installation CD, you can download a Vista Recovery Disc at the following link:
Windows Vista Recovery Disc [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) 

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Did I mention that you should backup important info first?:)

Should I burn the Vista recovery CD image to a DVD or will a CD-R be fine?

Also is there really much of an advantage of using GParted instead of the Ubuntu installer? Or is GParted just what I should use to resize it later if needed?

---

### Post by yanceypd on 2009-09-27
I don't know the size of the file recommended to you.  A real system disk is a DVD.  I'd let the installer disk do the work.  Probably safer than Gparted until you get some experience.  I screwed up a couple of times learning.  Good luck.:)

---

### Post by Chewy2 on 2009-09-27
OK, so I tried to install it with the Ubuntu installer. It didn't look like i could change the partition sizes. It just gave me the option to use the remaining free space(80MB), or select partitions manually(which I went into but I couldn't change the size of them).

So should I go ahead and use GParted to change the size of them or will that mess some things up? Is formatting going to be necessary here if I want to install Ubuntu?

---

### Post by oldfred on 2009-09-27
Gparted is the tool in the Ubuntu installer. It is just set up to work as part of the install. Often the install comes up with a default of 2.5GB but you have to use the slider to increase that to at least 8 or 10GB to have Ubuntu work.  

You can use the Gparted CD to make the space in advanced if your desire.

As with all computer systems there is more than one way to accomplish the task.

---

### Post by Chewy2 on 2009-09-27
Well I tried to use GParted to change it, but that couldn't even do it.

I think this might be because my HD was just about full at one point.

Am I going to have to format in order to get it to change?

EDIT: I'm gonna try and use perfectdisk to move all the files to the front of the disk...

---

### Post by theozzlives on 2009-09-27
80 GB is plenty to start with (on my test machine, I have Win XP and Ubuntu on a 40 GB HD). As far as sharing your files see [this]("http://ubuntuforums.org/showthread.php?t=1244185") thread, It was designed for XP but if you change Documents and Settings to Users it will work for Vista.

---

### Post by arpanaut on 2009-09-27
Your HD is about 80% full and most any file system is going to start getting crabby when you get that full and now you are trying to take another 10-15% away, so yeah windows partitioner isnt' going to want to do that.

You would be far better off moving 20-30 gig. of unused or little used data to your external then defrag a few times and see if Vista will comply. (You will be able to acess this data from both OS)

Make it easy on yourself.

Just my $.02

---

### Post by mtate5000 on 2009-09-27
Tiredbird made a good point about 5g being a good size. What I did is I have 150g hard drive and I created 3 primary partitions and an extended partition that constitutes the majority of my disk space. The 1st partition :Ubuntu 9.04(6g), 2nd: Win 7(20g), 3rd: osX86(15g), 4th is the extended partition. My 3 primaries are 41g of space and my extended is 119g partitioned as follows. 2g swap then 80 NTFS formatted partition. The rest of space are various partitions that I use to test other os's on. The NTFS partition I created is basically a home partion, though not technically. I use that as my all around media and document storage. I can access this partition easily from any operating system.
osX mounts it automatically, Windows lists it under "Computer" and I configured all of the linux distros to automount it at bootup. What you can do once youve defragged and all that crap is give yourself 5g for ubuntu, 2 for swap and whatever is left over a NTFS or FAT32 partition. That way you can easily transfer files from windows to NTFS (lets call it storage), and then use gparted in ubuntu to shrink windows and grow storage without having to use a live disc. All your files will be easily accessible from either os. You'll have to use synaptic to download all the NTFS plug-ins for gparted. For whatever reason they dont come stock. Just some food for thought.

---

### Post by Chewy2 on 2009-09-27
I tried to consolodate free space with PerfectDisk but there is a problem...

There are a fairly large number of excluded files at the end of the disk.

Here's a couple pictures displaying the excluded files:
[IMG]http://img.photobucket.com/albums/v38/ch3wy/excludedpt1.jpg[/IMG]
[IMG]http://img.photobucket.com/albums/v38/ch3wy/excludedpt2.jpg[/IMG]

And here is a picture of the drive map:
[IMG]http://img.photobucket.com/albums/v38/ch3wy/excludedpt3.jpg[/IMG]


Anybody know how to fix this?

---

### Post by oldfred on 2009-09-27
Some one had these comments:
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.

But as arpanaut said you do not have much space on this hard drive. Maybe its time for a second drive just so you have space to backup the important stuff.

---

### Post by Chewy2 on 2009-09-28
Alright so I disabled that stuff and got another 10GB free. Then I read that Acronis Disk Director worked loads better so I used that to free up yet another 10GB.

So now I just have to install it and I should be good to go. Thanks for your help everyone!

---

