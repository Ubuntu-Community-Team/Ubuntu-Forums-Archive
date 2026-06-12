---
title: "Lost a partition using format to....."
date: 2010-03-28
forum: New to Ubuntu
---

### Post by LearningPerson on 2010-03-28
My original 3 partition drive was running fine then I received Low Disk warnings for Karmic/SuperOS. I ran a liveCD of Gparted and tried to make Karmic larger.  I didn't understand how to enlarge it and did a "Format to...."   I just want my Linux sda6 enlarged, and also sda2 which is Windows 7.  I have searched all day for answers in the forums.

Here is the mess:

$ sudo fdisk -l

Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         784     6291456   27  Unknown 
Partition 1 does not end on cylinder boundary. 
/dev/sda2             784        3717    23558594    7  HPFS/NTFS 
/dev/sda3            3718       30401   214339230    5  Extended 
/dev/sda5           29835       30401     4554396   82  Linux swap / Solaris 
/dev/sda6           17134       29312    97827786   83  Linux 
/dev/sda7           29313       29834     4192933+  82  Linux swap / Solaris 
/dev/sda8           16604       17133     4257193+  82  Linux swap / Solaris 
/dev/sda9            3718       16072    99241474+  83  Linux 
/dev/sda10          16073       16603     4265226   82  Linux swap / Solaris 

Or see attachment.

Please help.  Thanks,  Sharon

---

### Post by undecim on 2010-03-28
If you formatted a partition, it's impossible to get it back.

There are some programs you can use if you need to recover certain files, but if a file isn't contigous on the disk, you probably won't get it back.

---

### Post by LearningPerson on 2010-03-28
> **undecim said:**
> If you formatted a partition, it's impossible to get it back.

There are some programs you can use if you need to recover certain files, but if a file isn't contigous on the disk, you probably won't get it back.

This is what I feared but thank you anyway.

Is there a good explanation for GParted somewhere?  I have looked at the Help files and they don't mean much.  How can I clean this up and just save Windows Vista?  

I do have a LiveCD for Karmic/SuperOS and have backed up my files.

Thanks again,  Sharon

---

### Post by 2hot6ft2 on 2010-03-28
There's not much chance short of using forensic data recovery tools and doubtful then after a format.
I'm curious as to why you have all those 4GB swap partitions. They appear to be all the same, a standard linux swap. All you need is 1. Whichever linux you boot will use it. They don't need need a personal swap partition each and are all most likely just using the first one and all the others are just sitting there taking up space.
I would keep 1 and free up that 12GB of disk space that's going to waste.

---

### Post by LearningPerson on 2010-03-28
> **2hot6ft2 said:**
> There's not much chance short of using forensic data recovery tools and doubtful then after a format.
I'm curious as to why you have all those 4GB swap partitions. They appear to be all the same, a standard linux swap. All you need is 1. Whichever linux you boot will use it. They don't need need a personal swap partition each and are all most likely just using the first one and all the others are just sitting there taking up space.
I would keep 1 and free up that 12GB of disk space that's going to waste.

Thank you for responding.  I have no idea why I have so many Swap files and will delete all but one.  Then how do I free up all the space that's called "Extended" and "Unallocated" for the Karmic/SuperOS I am using now plus Windows Vista (both of which come up on Boot which is good)?

---

### Post by 2hot6ft2 on 2010-03-28
> **LearningPerson said:**
> How can I clean this up and just save Windows Vista?
You could boot the livecd and right click on any swap partitions that have keys next to them and select "swapoff".
Once you do that if anything else has keys next to it right click on it and select "un-mount".
Leave the 2 partitions on the left alone as that is your Vista and its recovery partition.
Select the others one at a time and click on the delete icon or right click and select delete.
I would just leave it as empty space and create the new partition in Vista so it will be happy with it.

You should read and take notes of the section 16 in the grub 2 guide so you know how to restore the windows boot loader since you wont be able to boot vista until you fix it.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You'll need the vista installation cd/dvd.

---

### Post by 2hot6ft2 on 2010-03-28
> **LearningPerson said:**
> Thank you for responding.  I have no idea why I have so many Swap files and will delete all but one.  Then how do I free up all the space that's called "Extended" and "Unallocated" for the Karmic/SuperOS I am using now plus Windows Vista (both of which come up on Boot which is good)?
Thought you just wanted vista left?:confused:
Which one is the Karmic partition?
What I see is you have one that is "/" and one that is "/media/" and they are both ext4. Are those Karmic?

---

### Post by LearningPerson on 2010-03-28
> **2hot6ft2 said:**
> You could boot the livecd and right click on any swap partitions that have keys next to them and select "swapoff".
Once you do that if anything else has keys next to it right click on it and select "un-mount".
Leave the 2 partitions on the left alone as that is your Vista and its recovery partition.
Select the others one at a time and click on the delete icon or right click and select delete.
I would just leave it as empty space and create the new partition in Vista so it will be happy with it.

You should read and take notes of the section 16 in the grub 2 guide so you know how to restore the windows boot loader since you wont be able to boot vista until you fix it.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You'll need the vista installation cd/dvd.

Thanks,  I called the manufacturer and they have no Vista installation CD/DVD, only the Recovery partition which will hopefully leave just Vista and empty space.  The warning says all files will be lost but I have no files on Windows Vista anyway.  

I would then install the Ubuntu LiveCD and maybe have two large partitions?

---

### Post by 2hot6ft2 on 2010-03-28
> **LearningPerson said:**
> which will hopefully leave just Vista and empty space.
There it is again. Don't do anything to it until you decide what you want to do because you have me confused as to what that is.

---

### Post by 2hot6ft2 on 2010-03-28
FREE WINDOWS VISTA RECOVERY CD
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by LearningPerson on 2010-03-28
> **2hot6ft2 said:**
> Thought you just wanted vista left?:confused:
Which one is the Karmic partition?
What I see is you have one that is "/" and one that is "/media/" and they are both ext4. Are those Karmic?

I just wanted Vista left so I could re-install Karmic LiveCD - if I couldn't save either of my Karmics.   

Yes, one ext4 is my old lost formatted Karmic and the other ext4 is the Karmic I am using now.  Would be nice if I didn't need to "lose" or delete this one but I haven't many OO files as I just began this AM.....and am backing up on my thumb drive as I go along.

---

### Post by 2hot6ft2 on 2010-03-28
> **LearningPerson said:**
> I just wanted Vista left so I could re-install Karmic LiveCD - if I couldn't save either of my Karmics.   

Yes, one ext4 is my old lost formatted Karmic and the other ext4 is the Karmic I am using now.  Would be nice if I didn't need to "lose" or delete this one but I haven't many OO files as I just began this AM.....and am backing up on my thumb drive as I go along.
Now I get it.
See my last post for a free vista recovery cd you can download in case you ever need or want it.
Give me a couple minutes since I don't type all that fast.

---

### Post by 2hot6ft2 on 2010-03-29
So in that case here's what I would suggest.
Since you just started and don't have a bunch of things you can't live without on there yet.
I would do a fresh install like this.

Boot the livecd
Go to
System > Administration > GParted
and right click on any swap partitions that have keys next to them and select "swapoff".
Once you do that if anything else has keys next to it right click on it and select "un-mount".

**Leave the 2 partitions on the left alone as that is your Vista and its recovery partition.**

Select the others one at a time and click on the delete icon or right click and select delete.

Click on Apply.

That would just leave it as empty space after the vista partition and it's recovery partition.

Now create the partition layout the way you want it for Karmic plus one swap partition.

**OPTIONAL:** If you want a separate partition for /home then set up 2 partitions, 10GB should be ok for / and whatever you want for /home, /home is where all your configuration files are stored and everything in your Places > Home Folder including your desktop.

If you want to be able to store files on a partition that both vista AND ubuntu can access create a partition for just that purpose and choose NTFS for the file system type.

Once you have the partitions laid out the way you want click on Apply.

Now it should be laid out all nice and pretty the way you want it.
Close GParted

Double click on the ubuntu installer on the desktop.
When you get to the partitioner click on "Manual" (it's just above the bottom bar representing the drive) then on Forward.
That will load the manual partitioner.

Select the partition you want Karmic installed on and click on "Change" at the bottom.
File system type ext3 or ext4 your choice.
Mount point set to /
click on format then on Ok

**OPTIONAL:** If you chose to have a separate partition for /home set it up the same way EXCEPT set the mount point as /home

It will automatically detect the linux swap partition you already set up so that's it you can go thru the rest of the installer.

Since you're going to be installing Karmic again you wont need the vista recovery cd because it will reinstall the grub-pc boot loader.

P.S. A lot of people set up a separate /home partition but every time I try things don't work like they should.

---

### Post by 2hot6ft2 on 2010-03-29
Also I noticed that you had a partition that was for media.
Personally I would set up a NTFS partition that can be used by both ubuntu and vista and store my media on it.
That's how mine is set up.

Like I can have all my music on it and that way it can be played on either operating system without having to have it all in 2 places.

---

### Post by LearningPerson on 2010-03-29
Thanks so much!  After studying what you suggested and wrote I got everything up and going.  Learned much more about partitioning as well. 

Sure does make a difference to back everything up.

Sharon

---

### Post by 2hot6ft2 on 2010-03-29
> **LearningPerson said:**
> Thanks so much!  After studying what you suggested and wrote I got everything up and going.  Learned much more about partitioning as well. 

Sure does make a difference to back everything up.

Sharon
Glad to hear it. Now your disk partitions are nice and neat too.
If that means this is solved for you please mark the thread as Solved using the Thread Tools at the top of the thread.

You're welcome, and enjoy.

---

