---
title: "More Ubuntu disk space, please."
date: 2010-08-01
forum: New to Ubuntu
---

### Post by Paper Pusher on 2010-08-01
I'm confident that this a question that has been asked before, but I'm an absolute beginner and a slow learner.  I've searched previous threads, but none helped.

My desktop computer came with Microsoft Windows XP MCE.  I installed Ubuntu 9.10 DTE in a dual-boot configuration from CD. No WUBI.  I like Ubuntu so much, it's now my primary OS.

Now Ubuntu is warning me that I have only 2GB of 268GB of disk space left. What do I do?

I've run XP defrag three times and XP tells me that I have 82GB of 174GB left.  How do I transfer some of the 82GB from XP to Ubuntu?  

I know gparted has something to do with the solution to my problem.

I don't want to lose any of my data, but I can't run Simple Backup to DVD because I don't have enough disk space.

Help!

---

### Post by marshmallow1304 on 2010-08-01
It's good that you've already run defrag in XP.  Now, boot up the LiveCD you used to install Ubuntu and select the 'Try without making changes' option.  After it's booted, go to System->Administration->GParted (may be called Partition Editor or something similar).  Find your swap partition (linux-swap), right-click it, and click "Swapoff".  Now, find your Windows partition (ntfs), right-click and Resize/Move.  Use the sliders at the top to resize the partition - if Ubuntu is on the left take off space on the left or vice versa if it's on the right.  Then use the same method to expand the Ubuntu partition into the newly created free space.

Now click Apply and the operations will be performed.  This may take several hours depending on what needs to be done.


Note: If, once you've opened GParted, you're unsure of what to do, post a screenshot of it so we can see how your partitions are laid out.

---

### Post by Paqman on 2010-08-01
What to do depends on what is taking up all the space on your Ubuntu partition.

If it's all files and data you want to keep then sure, fire up your LiveCD and run Gparted to shrink your Windows partition and give more to Ubuntu.

You really, really need more space on your Ubuntu partition. Having it that full will be resulting in serious fragmentation of the filesystem, which is bad. Have a read of [this thread]("http://ubuntuforums.org/showthread.php?t=140920") to get rid of some of the baggage.

---

### Post by Paper Pusher on 2010-08-14
I have taken Paqman's advice and deleted remaining Ubuntu .iso files as well as following steps 1-3 of his link.  I now have 3.9GB of space free.

I have taken Marshmallow's advice and run geparted.  The screen shot is attached.
  
I'm not sure what to do.  Some tech types tell me that what I'm trying to do is impossible.  Is that right?

---

### Post by Darkness Des on 2010-08-14
It is not impossible. Actually, it is rather easy. Now, I want you to run these two commands to clear out your package cache. If you haven't been doing this already, it will REALLY fill up your system with downloaded packages.
```
sudo aptitude clean
sudo apt-get autoclean
```

---

### Post by sydbat on 2010-08-14
> **Paper Pusher said:**
> I have taken Paqman's advice and deleted remaining Ubuntu .iso files as well as following steps 1-3 of his link.  I now have 3.9GB of space free.

I have taken Marshmallow's advice and run geparted.  The screen shot is attached.
  
I'm not sure what to do.  Some tech types tell me that what I'm trying to do is impossible.  Is that right?It looks like you are running a couple of Linux distros, yes? If so, you do not have to create separate swap partitions for each...you can share one swap partition. Then you can remove the unused ones and increase the size of the other Linux partitions/decrease the size of your Windows partition.

Also, if you set up a separate /home partition, it too can be shared by several Linux distros.

---

### Post by Paper Pusher on 2010-08-14
> **sydbat said:**
> It looks like you are running a couple of Linux distros,

I am not intentionally running several distros.  I'm only running 9.10.
How do I fix this?

---

### Post by Paper Pusher on 2010-08-14
> **Darkness Des said:**
> I want you to run these two commands...

Done.  What do I do next?

---

### Post by john newbuntu on 2010-08-15
You appear to have several ext* filesystems on /dev/sda9, /dev/sda7 and /dev/sda5 partitions.  What are these?

Boot into Ubuntu, open a terminal (Applications->Accessories->Terminal) and run the command "df".  Please post the output of this command.

See if you can spot any of these partitions on the left column of the output.  Those are the only ones you will require for Ubuntu.  Now, it is possible that you might have at some point stored data in the others and have unmounted them or perhaps an install gone bad.  Do you remember doing this?  If so, do you need the data in those partitions?  Can you back them up?

Where I am getting at is that if you do not require at least one of those logical partitions /dev/sda5 through /dev/sda10, you could use that space for Ubuntu rather than(or in addition to) taking it from Windows.

Also post the output of the command "swapon -s" and indicate your RAM size.

---

### Post by Paqman on 2010-08-15
> **Paper Pusher said:**
> I am not intentionally running several distros.  I'm only running 9.10.
How do I fix this?

All you need to do is delete any unneeded partitions, then expand the ones you are using. You can do this in Gparted.

Make double sure you know what partitions you're using. That's the idea behind john newbuntu's instructions. Once you've identified which partitions are unnecessary and got rid of them you'll have more than enough space available.

However, before deleting anything, _take a backup_. Do not skip this step.

---

### Post by Paper Pusher on 2010-08-15
> **john newbuntu said:**
> You appear to have several ext* filesystems on /dev/sda9, /dev/sda7 and /dev/sda5 partitions.  What are these?
I really don't know, but I'm eager to learn.  Thanks for your help.

---

### Post by Paper Pusher on 2010-08-15
> **john newbuntu said:**
> Boot into Ubuntu, open a terminal (Applications->Accessories->Terminal) and run the command "df".  Please post the output of this command.
post the output of the command "swapon -s" and indicate your RAM size.

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda9             82021140  73617512   4237176  95% /
udev                   1545616       372   1545244   1% /dev
none                   1545616       244   1545372   1% /dev/shm
none                   1545616        88   1545528   1% /var/run
none                   1545616         0   1545616   0% /var/lock
none                   1545616         0   1545616   0% /lib/init/rw
/dev/sdf1              3908100      6252   3901848   1% /media/04C0-2649
/dev/sdd1               495168    171984    323184  35% /media/KODAK
/dev/sdg1            488384000 207565988 280818012  43% /media/OneTouch4
~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/sda10                              partition	3582452	0	-1

From System Monitor:
Ubuntu 9.10
Linux 2.6.31-22
GNOME 2.28.1
Memory: 2.9 GiB
availble Disk space: 4.0 GiB

---

### Post by Paper Pusher on 2010-08-15
> **Paqman said:**
> However, before deleting anything, _take a backup_. Do not skip this step.
I've installed Simple Backup, but it tells me that I don't have enough free disk space to run it!

Another new development.  Out of frustration, I've decided to buy my way out of my troubles.  A second internal hard drive is arriving via UPS on Tuesday.
Samsung SpinPoint F3 HD103SJ 1TB SATA2 7200rpm 32MB Hard Drive  	HD-HD103SJ

My power supply should be adequate.  I changed to support my graphics card.
Antec earthwatts EA500 500W ATX12V v2.0 Power Supply 100 - 240 V

I can dedicate the new drive to Ubuntu and leave the original 187GB NTFS + 9.5GB FAT32 to XP.

I have attached a screenshot for details.

Have I just created more trouble for myself?  Less than $60 shipped for a 1TB drive seemed reasonable.  But now I have to get Ubuntu off the main drive.

I notice from the screen shot that my main drive is a 
Barracuda 7200.11 SATA 3Gb/s 500-GB Hard Drive.

Ubuntu is now my main OS. XP is secondary.  How do I use the 1.5TB HDD space wisely

---

### Post by john newbuntu on 2010-08-16
From your "df" and "swapon" outputs, you would have noticed that only /dev/sda9 and /dev/sda10 matter to Ubuntu.  The rest /dev/sdf1, /dev/sdd1, /dev/sdg1 etc. I presume are some external devices/camera/usb sticks connected to the computer.  Please correct me if I am wrong here.

So, running GParted from a liveCD, you could safely drop /dev/sda5, sda6, sda7 and sda8.  Matter of fact you could even drop /dev/sda10 and click on apply.  This way, you will have over 270 GB for Ubuntu, which I hope is more than enough.  Make sure as marshmallow1304 pointed out to right click the swap partitions and click swapoff before deleting each of them.  Then extend your existing /dev/sda9 partition to occupy (almost) the whole of the 270GB.  Just leave about 4GB towards the end.  Hit apply.

Finally, create a small 4GB swap partition towards the end of your extended partition(/dev/sda3) and use it for Ubuntu swap.  You will have to edit your /etc/fstab from a liveCD and change the UUID of swap partition.  You can obtain this UUID value using the command "sudo blkid -c /dev/null" from a terminal in liveCD.

But I would still be curious to know what were in those partitions sda5 and sda7? Don't bother if it is not important.

Now as far as the new spin here goes - your Samsung SpinPoint F3 seems to be so much identical to Barracuda from a performance perspective (other than size of course).  You can obviously use this for backup or even create another distro(s) or if you are more adventurous, create a RAID1 on this drive for Ubuntu only.  I am not sure on why you bought this drive when you have enough space already on the Barracuda.  But it is your call.  All said and done, it is invaluable to at least clone your first disk to the new one and store it as an image.  Among the several tools available out there, clonezilla can help you with this.

---

### Post by Paper Pusher on 2010-08-16
> **john newbuntu said:**
> ... Now as far as the new spin here goes - your Samsung SpinPoint F3 seems to be so much identical to Barracuda from a performance perspective (other than size of course).  You can obviously use this for backup or even create another distro(s) or if you are more adventurous, create a RAID1 on this drive for Ubuntu only.  I am not sure on why you bought this drive when you have enough space already on the Barracuda.  But it is your call.  All said and done, it is invaluable to at least clone your first disk to the new one and store it as an image.  Among the several tools available out there, clonezilla can help you with this.

i didn't know the capabilities of my first drive when i ordered the samsung.  i would have saved myself the usd 60.  but now that's water under the bridge.

to turn the unnecessary samsung lemons into ubuntu lemonade, where can i read about using the ubuntu portion of the seagate 500gb drive for [software] raid1 with the samsung drive and use the remaining samsung space as regular ubuntu disk space?  you have a great idea there.

---

### Post by Paper Pusher on 2010-08-17
john,

great questions.  i'll answer tomorrow.

---

### Post by Paper Pusher on 2010-08-17
Thank you everyone for your advice and comments.  With your help, I'm able to reconstruct the following set of events.

1.  I buy a HP a1624n computer with XP and a 250GB disk.  Sector sda1 ntfs 174.23GB and sda2 recovery fat32 8.85GB.
2.  The disk crashes and I replace it with the 500GB Seagate. I use the recovery DVDs to reinstall XP.
3.  I install Ubuntu to try it out and upgrade it 6 months later, resulting in 9.10, all in sda3 282.68GB.  Somehow, this creates 3 installations:
   sda5 ext3 32.59GB and sda6 swap 1.44GB
   sda7 ext4 159GB and sda8 swap 6.76GB
   sda9 ext4 79.47GB and sda10 swap 3.42GB 9.10?
4. I choose Ubuntu as my main operating system and run out of disk space (now 4GB left).  Your excellent advice has little impact.  It is overwhelmed by the multiple Ubuntu installations.

Is this what probably happened?  
More questions to follow.

---

### Post by john newbuntu on 2010-08-17
Yep, that sums it up.  Didn't know that your disk had crashed at one point.
What Paqman and I were suggesting was to get rid of some of the unnecessary Ubuntu installs.

---

### Post by bradmayne04 on 2010-08-18
> **Darkness Des said:**
> It is not impossible. Actually, it is rather easy. Now, I want you to run these two commands to clear out your package cache. If you haven't been doing this already, it will REALLY fill up your system with downloaded packages.
```
sudo aptitude clean
sudo apt-get autoclean
```

but won't autoclean get rid of certain dependencies that you might need for programs that you need or want?  maybe I'm wrong on this so don't quote me. i've attempted to do a clean and seen samba stuff in there that I thought I would need to keep that working...  so in the end i didn't clean.

---

### Post by Paqman on 2010-08-18
> **bradmayne04 said:**
> but won't autoclean get rid of certain dependencies that you might need for programs that you need or want?  maybe I'm wrong on this so don't quote me. i've attempted to do a clean and seen samba stuff in there that I thought I would need to keep that working...  so in the end i didn't clean.

No, it only gets rid of the old .deb files from the package manager's cache. The actual apps are installed and won't be touched. If you just use apt-get autoclean it also only gets rid of .debs that are obsolete (ie: it will retain .debs for the current version of a package, but will remove ones for previous versions), so there's absolutely no down side to doing it. Using apt-get clean deletes the whole cache, so there's no point running autoclean if you've already run clean.

---

### Post by Paper Pusher on 2010-08-19
First of all, I want to thank all of you for your  help and advice.  I now know what to do (I think).

I still have some questions, though.

1.How did my install of 9.4 and update to 9.10 turn into two installs of  9.10 and one of 9.4?
2.Why are the file system partitions sda5, sda7, and sda9 so dramatically different in size?
3.Partition sda7 is particularly large.  How do I examine sda7 to see what's inside?   Browsing for /etc/sda7 yields a file, not a file system.
4.All of you advised that I back up my work.  But how do I do that if  Simple Backup refuses to run for lack of available disk space?  Is this where clonezilla live fits in?
5.As I upgrade to 10.4, how can I prevent inadvertently creating another distro inside sda3?
6.In an earlier post, John suggested that I use my new 1TB Samsung in a RAID1 configuration with 300GB partition sda3 (cleansed of the two extra distros).  The remaining 700GB of the Samsung would be non-RAID.  Where can I read more about this scenario?

---

### Post by Paper Pusher on 2010-08-19
> **john newbuntu said:**
> From your "df" and "swapon" outputs, you would have noticed that only /dev/sda9 and /dev/sda10 matter to Ubuntu.  The rest /dev/sdf1, /dev/sdd1, /dev/sdg1 etc. I presume are some external devices/camera/usb sticks connected to the computer.  Please correct me if I am wrong here.

Yes, you are correct.  They are an external USB hard drive, SD card, and memory stick.

---

### Post by john newbuntu on 2010-08-19
> **Paper Pusher said:**
> 
1.How did my install of 9.4 and update to 9.10 turn into two installs of  9.10 and one of 9.4?
No clue.  My guess would be a couple of failed installs. Or did someone else use your machine?

> 
2.Why are the file system partitions sda5, sda7, and sda9 so dramatically different in size?Absolutely no clue.  Please check the contents.
> 3.Partition sda7 is particularly large.  How do I examine sda7 to see what's inside?   Browsing for /etc/sda7 yields a file, not a file system.If you are unable to see /dev/sda7 already under the Places menu, open up a terminal and run:
```
sudo mkdir /mnt/mysda7
sudo mount -t ext4 /dev/sda7 /mnt/mysda7
```Now go to /mnt/mysda7 using "gksu nautilus" and inspect the files.  After you are done inspecting:
```
sudo umount /dev/sda7
```>  4.All of you advised that I back up my work.  But how do I do that if  Simple Backup refuses to run for lack of available disk space?  Is this where clonezilla live fits in?In general, it is good to have an external drive for backups. I am not  sure about simplebackup.  But you could create an image of your partition  using clonezilla for instance and you could use /dev/sda1 for housing  the image temporarily.
>  5.As I upgrade to 10.4, how can I prevent inadvertently creating another distro inside sda3?Ubuntu upgrades, as far as I know do not create new partitions, unless there is/was an option that I am unaware of.
>  6.In an earlier post, John suggested that I use my new 1TB Samsung in a RAID1 configuration with 300GB partition sda3 (cleansed of the two extra distros).  The remaining 700GB of the Samsung would be non-RAID.  Where can I read more about this scenario?Google is your friend.  This is essentially setting up mirroring with software raid.  You  have to understand the consequence of this. Only a portion of the two disks will be mirrored.  I'll leave the choice to you on whether you really need RAID, but  please read up on it before venturing into it.  Here's one post I found  in google on this:
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

---

### Post by Paper Pusher on 2010-08-19
John,

Thanks for the quick reply.


1.nobody's been using my machine.
2. 
3.Thanks.  I'll try this in the morning.
4.Good idea.  A 2tB external drive is on its way.
5.I'll monitor it closely this time using the techniques you taught me.   I'll report back.
6.Thanks for the great link.  Here's what  I'm using:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")
           I'm impressed that Ubuntu can do this.  Having lost the first drive makes me more sensitive.  The usual backup techniques don't work well with today's large drives.  $90 = 2TB = 425DVDs.

---

### Post by Paper Pusher on 2010-08-22
i examined sda5 and sda7 using john's technique.  thanks, john.

there seem to be 3 complete ubu distros, each with user data; 5 7 and 9.
sda7 is dated feb 25 2010.  the others have more varied dates.  very puzzling.

i will back up /home for sda7 and clone the entire disk with clonezilla before making any gparted changes.

wish me luck.

---

