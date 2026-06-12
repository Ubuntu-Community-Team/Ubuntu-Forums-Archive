---
title: "Starting Over"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by DGINSD on 2011-03-12
I'm starting over I've wiped my Ubuntu install on my Dell Inspiron 1150 and rolled back my MBR. So now I have an 80Gig hard drive (76Gig actually I got ripped off on space) 40 Gig of which is occupied by a primary partition with Windows XP installed the other 36Gig is an extended partition and nothing else (no logicals set up in it).
 
So some questions I want to install Ubuntu 10.10 that I downloaded and burned to DVD on my extended partition with a seprate home partition with only 36Gigs to work with. 
 
What size should everything be? Home, Root, and Swap?
 
Any bennifit making my swap larger than my RAM (size very small 527M)
 
Is the DVD capeable of setting up and sizing the seprate partitions durring install like I want, or do I need to do all that prior using my windows partition editor?
 
Next I noticed when Ubuntu was mounted I could see and deal with my windows NTFS
 but when my Windows XP was mounted it was as the partition didn't exist. Should or could I use another files system to change this and what are the pros and cons of doing such? If its too much to explain a link for some reading would do nicely or a brief explanation?
 
I decided to start over because I just had too much goofieness with the system and needed to start over and not make mistakes I made the first time around. If theres anything anyone can think of that I may be neglecting or other set uppractices that may be helpful please let me know. I'm a very new noob but I'm learning.

---

### Post by fabricator4 on 2011-03-12
> **DGINSD said:**
> I'm starting over I've wiped my Ubuntu install on my Dell Inspiron 1150 and rolled back my MBR. So now I have an 80Gig hard drive (76Gig actually I got ripped off on space) 


You didn't get ripped off.  Well you did, but only by the HDD manufacturers marketing tactics.  Manufacturers use figures which suggest that 1 GB = 1,000,000,000 bytes, which isn't true.  They all do it.


> 


40 Gig of which is occupied by a primary partition with Windows XP installed the other 36Gig is an extended partition and nothing else (no logicals set up in it).
 
So some questions I want to install Ubuntu 10.10 that I downloaded and burned to DVD on my extended partition with a seprate home partition with only 36Gigs to work with. 
 
What size should everything be? Home, Root, and Swap?


It really depends on how you want to use the machine.  Ubuntu will install in less than 4 GB, but you wouldn't be able to do a lot with it.  10 GB is too small if you want to try out a lot of programs and play with the system.  15 GB is useful for almost anything you will use / "root" for.  The use of swap file depends on how you intend to use the machine.  If you're editing huge images for example, you're going to need more swap.  If you want to be able to suspend the machine you'll need a swap big enough to copy the entire RAM to plus whatever else may be in the swap, to keep from shooting yourself in the foot.  My 900SD has 1 GB RAM but space is short: the swap file is 384 MB and it suspends fine, but I am a little bit careful about how I use it.

The rest of your partition of course can be /home, A little less than 20 GB, give or take.

> 
Any bennifit making my swap larger than my RAM (size very small 527M)


Not really, except for the provisos listed above. If space is tight, keep the swap partition small, but do keep an eye on RAM usage.


> 
 
Is the DVD capeable of setting up and sizing the seprate partitions durring install like I want, or do I need to do all that prior using my windows partition editor?


Yes it is, but many of us prefer to set up the partitions first using Gparted on the LiveCD.  I find Gparted easier to use, plus if your swap partition is already set up then the installer will use it, which can speed things up a bit. Even if you do this though, you still have to deal with the partition program in the installer, to specify mount points and filesystems etc.

> 
Next I noticed when Ubuntu was mounted I could see and deal with my windows NTFS


Yes, Ubuntu will see and use a variety of filesystems, including NTFS, W95, FAT32 etc.

> 
 but when my Windows XP was mounted it was as the partition didn't exist. Should or could I use another files system to change this and what are the pros and cons of doing such? If its too much to explain a link for some reading would do nicely or a brief explanation?


I _think_ what you're asking is if Windows will be able to access your ext4 home partition.  Yes, but you need to install an opensource filesystem driver called "ext2".  Don't worry, ext4 partitions are backwards compatible with ext2, so you'll be able to access and use your /home partition fine.
 
> 
I decided to start over because I just had too much goofieness with the system and needed to start over and not make mistakes I made the first time around. If theres anything anyone can think of that I may be neglecting or other set uppractices that may be helpful please let me know. I'm a very new noob but I'm learning.

Well, it sounds like you are making a good (second) start.  You learn **more** (edited) by breaking a system and fixing it than you do by being to scared to play with it.

Just a couple of things:

You'll need to partition the unallocated 36 GB on the drive with an extended partition of 36 GB **if you don't already have one**. (edited) This is what the installer would do if you chose the "install alongside" option.  This extended partition is necessary.  The other three partitions, / /home and swap are set up as "logical" partitions, which will become obvious when you set them up in Gparted.

Secondly, if you haven't already erased your existing / partition, get a copy of the .deb files which you will find in /var/cache/apt/archives.

These are the install files that automatic updates and the software installer download.  If you put them back in /var/cache/apt/archives as soon as you are finished the install, Ubuntu will not have to download them all over again.  This is helpful if you have a limited amount of bandwidth per month.

I maintain three machines and multiple distros, and this saves me heaps of download, especially if I'm setting up from scratch.

Edit:
You might notice that last time you ran the installer it left some unallocated space after your Windows primary partition.  This is because the partition size is locked to the cylinder size (I think).  Delete this extended partition (you'll have to delete the logical partitions first) and recreated it without the cylinder limitation. Apply the changes at this point, otherwise Gparted will resize the extended partition so that it leaves the unallocated space once again, and the logical partitions will not be created due to an error.

Chris

---

### Post by ajgreeny on 2011-03-12
The best way in your situation would probably be to:-

1.  Make a backup of all your data filesthat at the moment are in the windows XP partition, ie, probably in "My Documents",  that will include your docs, music, videos, etc etc, to an external disk.

2.  Delete all those files now backed up and then defrag XP a couple of times.

3.  Using the live CD/DVD of 10.10 go to System ->Administration ->Gparted and shrink the XP partition but you must leave space for system activities and future defrags etc of about 50% of the used space. So if XP now uses 15GB make the partition about 22.5GB.

4.  Enlarge the extended partition to fill the unallocated space with gparted.

5.  In the large extended partition, again with gparted, make logical partitions of 
a) about 7 or 8 GB for root as ext4.
b) about 2GB for swap.
c) the rest for data formatted as ntfs.

5.  Copy all the backed up files and folders to the data partition.

6.  Install ubuntu, choosing the advanced (but easy) partitioning option, and set the partitions as I mentioned above for root and swap.

7.  After installing ubuntu, add ntfs-config to allow the mounting read/write of the data partition at boot time.

With the size of disk you have, I wonder if a separate /home is the best way forward; it is usually the data files that are so important, not the configuration files and folders.  The hidden .mozilla and .thunderbird folders with all your bookmarks and emails can be kept on the windows partition and read from ubuntu if needed; have a search for shared configurations and profiles.  [http://www.google.com/url?q=https://help.ubuntu.com/community/Thunderbird&sa=U&ei=ewB8TffEAcnO4gaX18iKBg&ved=0CDMQFjAF&usg=AFQjCNGTPU5AKKzUQ2_-topqNKS4vBiQgA](http://www.google.com/url?q=https://help.ubuntu.com/community/Thunderbird&sa=U&ei=ewB8TffEAcnO4gaX18iKBg&ved=0CDMQFjAF&usg=AFQjCNGTPU5AKKzUQ2_-topqNKS4vBiQgA)

If you do things this way you will be able to read and write all your data files with both OSs, as they are on a ntfs partition.  If you had a separate /home partition, which would have to be a linux file system, not ntfs, windows would not be able to read or write to it, so it would be a lot less useful to you.

I hope that helps you, and is not too confusing.

---

### Post by DGINSD on 2011-03-12
OK first rather large stumbleing block Gparted is not seeingmy windows partition all it is seeing is my HDD as one large 74.53GiB unallocated spot with a warning "Invalid partition table on /dev/sda-wrong signature 0."  Help I'm lost now
 
BTW Thank you very much for the previous post Very very helpful

---

### Post by fabricator4 on 2011-03-12
> **DGINSD said:**
> OK first rather large stumbleing block Gparted is not seeingmy windows partition all it is seeing is my HDD as one large 74.53GiB unallocated spot with a warning "Invalid partition table on /dev/sda-wrong signature 0."  Help I'm lost now

Oh, that's nasty.  The problem is, if you do the wrong thing at this point, you'll lose the windows NTFS partition which should be the first primary partition on the drive.

You could try [testdisk]("http://packages.ubuntu.com/lucid/testdisk") to see if it will get the partition table back.

I hope that you followed ajgreeny's advice to backup all your data.  Any idea what might have happened to damage the partition table?

Chris

---

### Post by DGINSD on 2011-03-12
> **fabricator4 said:**
> Oh, that's nasty. The problem is, if you do the wrong thing at this point, you'll lose the windows NTFS partition which should be the first primary partition on the drive.
 
You could try [testdisk]("http://packages.ubuntu.com/lucid/testdisk") to see if it will get the partition table back.
 
I hope that you followed ajgreeny's advice to backup all your data. Any idea what might have happened to damage the partition table?
 
Chris
 
Thats what's odd I can start up XP just fine. 
 
I used a bootable CD to wipe the orginal Ubuntu install and remove grub from the MBR. I tested windows immediately after all was well booted right up.
 
Heres another oddity Gparted wont see my windows partition but the Disc utility sees a NTFS 42Gig partition WTH

---

### Post by DGINSD on 2011-03-12
Heres my real dilema how can I set up a new dual boot if Gparted cant see the windows MBR and existing partition? Where can it insert GRUB?

---

### Post by DGINSD on 2011-03-12
> **fabricator4 said:**
> Oh, that's nasty. The problem is, if you do the wrong thing at this point, you'll lose the windows NTFS partition which should be the first primary partition on the drive.
 
You could try [testdisk]("http://packages.ubuntu.com/lucid/testdisk") to see if it will get the partition table back.
 
I hope that you followed ajgreeny's advice to backup all your data. Any idea what might have happened to damage the partition table?
 
Chris
 
Sorry took Testdisk a while to compute how can I run it is it on my Ubuntu install CD? Or can I download and install mind you I'd have to download to a USB cause internet doesn't work on the CD boot. And I'm wayno good at installing manually.

---

### Post by fabricator4 on 2011-03-12
> **DGINSD said:**
> I used a bootable CD to wipe the orginal Ubuntu install and remove grub from the MBR. I tested windows immediately after all was well booted right up.


Ah, what "bootable CD" did you use to remove the logical partitions that Ubuntu was on?  It seems like it has written something odd in the partition table that Gparted is not recognising.

>  
Heres another oddity Gparted wont see my windows partition but the Disc utility sees a NTFS 42Gig partition WTH
[/quote]

Obviously the two programs are working in slightly different ways.  There's a couple of different ways you could proceed here:

*) Find a different program that recognises the NTFS partition to do the partitioning with: Hopefully, if it re-writes the partition table correctly then Gparted will again be able to see it.  This isn't critical but I find it of concern that Gparted cannot read the partition table when it should be able to.

*) Boot the LiveCD and run the [bootinfo script]("http://ubuntuforums.org/showthread.php?t=1291280") to see what it thinks is going on.  Start a new thread and post the RESULTS.txt from bootinfo script to see if anyone has a safe way of repairing the partition table.

*) Forget Gparted and and start the install.  Do the partitioning manually when you are given the option (do not proceed if the manual install partitioner does not recognise the NTFS partition) and hope it all comes out in the wash - ie that the partition table gets re-written correctly.

*) Try booting a Windows recovery console from the Windows installation disks.  Run "fixboot" and and see if that fixes up the partition table.

Which way you decide to use will depend very much on how important the NTFS partition is to you.  Obviously if you really need Windows and you've got no way of re-install it at this time, you won't want to do anything that will cause it go missing.


Chris

---

### Post by fabricator4 on 2011-03-12
> **DGINSD said:**
> Sorry took Testdisk a while to compute how can I run it is it on my Ubuntu install CD? Or can I download and install mind you I'd have to download to a USB cause internet doesn't work on the CD boot. And I'm wayno good at installing manually.

Well the easiest thing would be to install it into a LiveCD session.  It should work.  Of course, it will disappear again as soon as you shut down, however if you copy the .deb files in /var/cache/apt/archives you'll be copying the the install files.  Keep them handy and copy them back again if you want to re-install testdisk later, that way you don't have to download it each time.

Not having had to use testdisk, I'm not sure how safe it is to use it in this case.  You'll have to judge the advisability of running this program - I can't say whether it's going to work as described on the box and I advise you proceed with caution. ;-)

Chris.

---

### Post by DGINSD on 2011-03-13
> **fabricator4 said:**
> Ah, what "bootable CD" did you use to remove  the logical partitions that Ubuntu was on?  It seems like it has  written something odd in the partition table that Gparted is not  recognising.

Obviously the two programs are working in slightly different ways.  There's a couple of different ways you could proceed here:

1) Find a different program that recognises the NTFS partition to do the  partitioning with: Hopefully, if it re-writes the partition table  correctly then Gparted will again be able to see it.  This isn't  critical but I find it of concern that Gparted cannot read the partition  table when it should be able to.

2) Boot the LiveCD and run the [bootinfo script]("http://ubuntuforums.org/showthread.php?t=1291280")  to see what it thinks is going on.  Start a new thread and post the  RESULTS.txt from bootinfo script to see if anyone has a safe way of  repairing the partition table.

3) Forget Gparted and and start the install.  Do the partitioning  manually when you are given the option (do not proceed if the manual  install partitioner does not recognise the NTFS partition) and hope it  all comes out in the wash - ie that the partition table gets re-written  correctly.

4) Try booting a Windows recovery console from the Windows installation  disks.  Run "fixboot" and and see if that fixes up the partition table.

Which way you decide to use will depend very much on how important the  NTFS partition is to you.  Obviously if you really need Windows and  you've got no way of re-install it at this time, you won't want to do  anything that will cause it go missing.


Chris



Sorry I took so long to get back, lots of work to do.

 In short a combination of  the tips you listed in order #4 #1 and #3  worked to get my MBR back and recognized by the install application.   All seems well again and this was definitely a learning experience. Thank you very very much for your tips I would of been lost without them.

I had to do a ton of stuff to get all this done and it took me almost  all night and some of this morning (my wife is ready to kill me). Here  is what I did hope this helps someone.

I have no Microsoft recovery CD, as this is a hand me down Dell Inspiron  1150, so first off it didn't come with a real one, and secondly the one  it did come with wasn't given to me.  If anyone is running XP and does  not have a recovery CD there is a way to get and burn a disc that at  least gives you access to Microsofts recovery console. I'd give the link  but my wife has since closed my web browser, and is using the computer I  was on. If you google "Recovery console without CD" and dig through th  first page of hits you should find some info about a download of 6  floppies from MS that someone figured a way to make into a bootable  disc. If you have trouble finding it PM me and I'll see if I can help.

Next I used "Aiome partition editor" for windows to set up my three new  logical partitions for the Ubuntu install. I'm sure this could of been  done better and easier with Gparted but as I said in earlier posts it  wasn't seeing my windows partition. This is a free program I downloaded  on-line and seems to work well. I set up 2 extended partitions of 16.5G  each and 1 for swap at 1.5G all unformatted as this partition editor  doesn't format Linux file systems.

After I set up the partitions I rebooted to the live CD and started the  Ubuntu install like I had numerous time before, but this time the  install program recognized my windows partition and the others I  created. So I selected the last option on which way to install, the one  that allows you to define the partitions for the install of Ubuntu. 

1) Select each partition and set its file type (I set mine to EXT4).

2) Click on the format check box and in the space below define the first  unformatted partition as "/home", the next partition as "/" (which is  root) and the last partition as the Linux swap space.

Hit install and let it do it's thing, reboot and all was well.

I listed all this because I had trouble finding clear documentation on  how to set up this way so I'm hoping someone else may stumble upon it  and find it useful to them.

A few thing thats are more specific issues to my computer, I had to get  the  proprietary broadcom drivers for my wifi card to be conected to do  updates, Once I did that when downloading the updates my wifi card would  only download a little bit at a time then disconnect on its own. I had  to click on the wireless connection applet, turn off wifi, turn wifi  back on, then click back on to the network I use for it to continue  downloading the updates. After the updates finished downloading and  applying the wifi card would stay connected just fine. This took a long  time with me in front of the computer repeating the above actions, I had  to do the same with my first install as well, but again I'm bringing it  up in case someone else finds the info useful (hopefully I'm the only  one that had to go through this (twice) but who knows), or perhaps for  those smarter than me to develop a  work around if this is a common  issue.

Again Fabricator4, Thank you very much I may have never gotten this figured out if you hadn't chimed in.

---

### Post by fabricator4 on 2011-03-13
> **DGINSD said:**
> 
A few thing thats are more specific issues to my computer, I had to get  the  proprietary broadcom drivers for my wifi card to be conected to do  updates, Once I did that when downloading the updates my wifi card would  only download a little bit at a time then disconnect on its own. I had  to click on the wireless connection applet, turn off wifi, turn wifi  back on, then click back on to the network I use for it to continue  downloading the updates. After the updates finished downloading and  applying the


Here's tip: take a copy of the .deb files in /var/cache/apt/archives.  These are the deb files that get downloaded for installation.  (I think I mentioned this one already, Oh well, I'll mention it again)  If you ever need to re-install in the future it sounds like it will save you heaps of time not having to download the initial updates ;-)

Chris

---

### Post by DGINSD on 2011-03-13
> **fabricator4 said:**
> Here's tip: take a copy of the .deb files in /var/cache/apt/archives.  These are the deb files that get downloaded for installation.  (I think I mentioned this one already, Oh well, I'll mention it again)  If you ever need to re-install in the future it sounds like it will save you heaps of time not having to download the initial updates ;-)

Chris Indeed you did mention it before, unfortunately for me I didn't read it till after I had wiped my original Ubuntu install. Thats what I get for being impatient, but I've noted it for future reference.  A quick question about that though. wouldn't doing this also import all the problems I was having?

On to my next step getting the restricted video codecs, and hopefully getting multimedia DVDs and what not playing smoothly. Hopefully I don't run into any more issues and everything else goes as planned.

---

### Post by fabricator4 on 2011-03-13
> **DGINSD said:**
> Indeed you did mention it before, unfortunately for me I didn't read it till after I had wiped my original Ubuntu install. Thats what I get for being impatient, but I've noted it for future reference.  A quick question about that though. wouldn't doing this also import all the problems I was having?

No, the .deb installation files will just sit there until you install them.  They won't do anything at all by themselves except take up a little disk space. When you go to Software Center or do an update, the system will use the .deb files in that directory instead of downloading them.  Of course if you somehow go a broken deb file on the system this would be bad thing, in which case downloading again would be advised.

I think the system checks the deb files before installing however - someone else might be able to verify this - it might be part of the .deb packaging.

Chris

---

### Post by DGINSD on 2011-03-15
Ok so all is still well but I have a question about kernels (actually I have quite a few but little time right now).

So in the thread "New to Ubuntu Start Here" sticky, on the second page post number 18, tip number 10, it talks about getting a new Kernel for those with Intel Pentium 2 or higher. I have a Pentium 4 mobile but I did a search in synaptic for "linux-image" and it brought up a few other kernel images but I didn't see any info regaurding the "linux-image 686" which the post says is vthe most likely one. How do locate it and once found how best to implement it? Is this post correct? and are there real bennifits to changing the kernel.

Maybe some further reading on this subject is in order, if someone has a few links I'd be very greatful if you would share 'em.

---

### Post by ajgreeny on 2011-03-15
> **DGINSD said:**
> Ok so all is still well but I have a question about kernels (actually I have quite a few but little time right now).

So in the thread "New to Ubuntu Start Here" sticky, on the second page post number 18, tip number 10, it talks about getting a new Kernel for those with Intel Pentium 2 or higher. I have a Pentium 4 mobile but I did a search in synaptic for "linux-image" and it brought up a few other kernel images but I didn't see any info regaurding the "linux-image 686" which the post says is vthe most likely one. How do locate it and once found how best to implement it? Is this post correct? and are there real bennifits to changing the kernel.

Maybe some further reading on this subject is in order, if someone has a few links I'd be very greatful if you would share 'em.
That post is now 3 years old and has been overtaken by kernels that do not really need any changing from machine to machine in normal situations, and as you say, there are no 686 kernels available now.

Don't worry; just go with the default kernel for your system, both  32 or 64 bit are included, and forget the rest.

---

