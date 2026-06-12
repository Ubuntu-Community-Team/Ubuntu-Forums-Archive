---
title: "Some Questions Before Installing Ubuntu"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-07
ok i am about to install Ubuntu 10.04 with STANDARD dual boot set-up (No Wubi, No Virtual Machine). Existing OS being Windows 7. But some questions need to be answered before this.

I have existing 5 partitions.
		C: 32GB NTFS (Primary)
		D: 32GB NTFS (Logical)
		E: 32GB NTFS (Logical)
		F: 32GB NTFS (Logical)
		G: 21GB NTFS (Primary)
		
I am windows expert but absolute beginner when it come to Linux. So far i have installed ubuntu only once on virtual machine, just a couple of weeks ago.

My plan is to install ubuntu on G partitions (if my guess is correct, it would be sda4 during ubuntu installation). I will install root, home and swap all by dividing G partition. And I prefer manual partitioning over all other options.

My questions are:
1. Is it necessary for ubuntu to be installed on a primary partition?

2. Is 21GB space enough for ubuntu 10.04? Will it effect ubuntu's running speed and performance? (Since My primary OS will still be Windows because other family members who are extreme novice will be using my computer for watching youtube videos. So i am forced to install ubuntu on as less space as possible.)

3. Should I still defragment all the partitions, even if the partition i am going to install ubuntu on is totally empty? (personally i don't see any need for doing so)

4. Should I still shrink one of the partitions? (personally i don't see any need for doing so)

5. I want F: partition to be accessible from both Operating Systems. So should I format it with fat32? Or NTFS still has advantage in this scenario? (i already know fat32 is not a journaling FS. But for a couple of reasons i want to format F: with FAT32)

6: If I format F: with FAT32, is it necessary to format it from ubuntu installer or window disk management? Can't I format it from anywhere i prefer? (I want F to be accessible from both OS BY DEFAULT. I don't want to install some other program to handle this issue)

7. Is Lucid Lynx's manual partitioning same as that of Karmic Koala? (All the videos that i watched to understand manual partitioning were about karmic koala, so it might be difficult for me to install Lucid Lynx if its manual partitioning is any different from karmic koala.)

---

### Post by Peter09 on 2010-05-07
Have Lucid installed on an 8GB SSD, so you should be OK with your G partition.

---

### Post by mikewhatever on 2010-05-07
> **SKhan said:**
> 
1. Is it necessary for ubuntu to be installed on a primary partition?
No. A logical partition is fine.

> 2. Is 21GB space enough for ubuntu 10.04? Will it effect ubuntu's running speed and performance? (Since My primary OS will still be Windows because other family members who are extreme novice will be using my computer for watching youtube videos. So i am forced to install ubuntu on as less space as possible.)

20+GB is plenty. The default installation only takes about 3.5GB.

> 3. Should I still defragment all the partitions, even if the partition i am going to install ubuntu on is totally empty? (personally i don't see any need for doing so)
No.

> 4. Should I still shrink one of the partitions? (personally i don't see any need for doing so)
No, since you seem to have the space ready for Ubuntu. Right?

> 5. I want F: partition to be accessible from both Operating Systems. So should I format it with fat32? Or NTFS still has advantage in this scenario? (i already know fat32 is not a journaling FS. But for a couple of reasons i want to format F: with FAT32)
Both FAT32 and NTFS should be fine. One other disadvantage of fat32 is the 4GB file size limit.

> 6: If I format F: with FAT32, is it necessary to format it from ubuntu installer or window disk management? Can't I format it from anywhere i prefer? (I want F to be accessible from both OS BY DEFAULT. I don't want to install some other program to handle this issue)
Format however you want, it doesn't matter.

> 7. Is Lucid Lynx's manual partitioning same as that of Karmic Koala? (All the videos that i watched to understand manual partitioning were about karmic koala, so it might be difficult for me to install Lucid Lynx if its manual partitioning is any different from karmic koala.)
Yes, it is the same.

---

### Post by sandyd on 2010-05-07
> **SKhan said:**
> ok i am about to install Ubuntu 10.04 with STANDARD dual boot set-up (No Wubi, No Virtual Machine). Existing OS being Windows 7. But some questions need to be answered before this.

I have existing 5 partitions.
        C: 32GB NTFS (Primary)
        D: 32GB NTFS (Logical)
        E: 32GB NTFS (Logical)
        F: 32GB NTFS (Logical)
        G: 21GB NTFS (Primary)
        
I am windows expert but absolute beginner when it come to Linux. So far i have installed ubuntu only once on virtual machine, just a couple of weeks ago.

My plan is to install ubuntu on G partitions (if my guess is correct, it would be sda4 during ubuntu installation). I will install root, home and swap all by dividing G partition. And I prefer manual partitioning over all other options.

My questions are:
1. Is it necessary for ubuntu to be installed on a primary partition?
**no. just delete G: and tell ubuntu to install on largest block of free space when you get to the partitioning stage.**
2. Is 21GB space enough for ubuntu 10.04? Will it effect ubuntu's running speed and performance? (Since My primary OS will still be Windows because other family members who are extreme novice will be using my computer for watching youtube videos. So i am forced to install ubuntu on as less space as possible.)
**It won't affect performance in the least, unless you run out of disk space :mad:**
3. Should I still defragment all the partitions, even if the partition i am going to install ubuntu on is totally empty? (personally i don't see any need for doing so)
**nope**
4. Should I still shrink one of the partitions? (personally i don't see any need for doing so)
**nope**
5. I want F: partition to be accessible from both Operating Systems. So should I format it with fat32? Or NTFS still has advantage in this scenario? (i already know fat32 is not a journaling FS. But for a couple of reasons i want to format F: with FAT32)
**NTFS works fine.**
6: If I format F: with FAT32, is it necessary to format it from ubuntu installer or window disk management? Can't I format it from anywhere i prefer? (I want F to be accessible from both OS BY DEFAULT. I don't want to install some other program to handle this issue)
**see above**
7. Is Lucid Lynx's manual partitioning same as that of Karmic Koala? (All the videos that i watched to understand manual partitioning were about karmic koala, so it might be difficult for me to install Lucid Lynx if its manual partitioning is any different from karmic koala.)
**Also see above (#1)**

.

---

### Post by nothingspecial on 2010-05-07
> **SKhan said:**
> ok i am about to install Ubuntu 10.04 with STANDARD dual boot set-up (No Wubi, No Virtual Machine). Existing OS being Windows 7. But some questions need to be answered before this.

I have existing 5 partitions.
		C: 32GB NTFS (Primary)
		D: 32GB NTFS (Logical)
		E: 32GB NTFS (Logical)
		F: 32GB NTFS (Logical)
		G: 21GB NTFS (Primary)
		
I am windows expert but absolute beginner when it come to Linux. So far i have installed ubuntu only once on virtual machine, just a couple of weeks ago.

My plan is to install ubuntu on G partitions (if my guess is correct, it would be sda4 during ubuntu installation). I will install root, home and swap all by dividing G partition. And I prefer manual partitioning over all other options.

My questions are:
1. Is it necessary for ubuntu to be installed on a primary partition?
I don`t think so but I have never tried.

> 2. Is 21GB space enough for ubuntu 10.04? Will it effect ubuntu's running speed and performance? (Since My primary OS will still be Windows because other family members who are extreme novice will be using my computer for watching youtube videos. So i am forced to install ubuntu on as less space as possible.)

I use between 6 and 7 gigs for Ubuntu

> 3. Should I still defragment all the partitions, even if the partition i am going to install ubuntu on is totally empty? (personally i don't see any need for doing so)

You don`t need to.

> 4. Should I still shrink one of the partitions? (personally i don't see any need for doing so) What for?

> 5. I want F: partition to be accessible from both Operating Systems. So should I format it with fat32? Or NTFS still has advantage in this scenario? (i already know fat32 is not a journaling FS. But for a couple of reasons i want to format F: with FAT32) Ubuntu will read both quite happily although linux file permissions wiil not work.

> 6: If I format F: with FAT32, is it necessary to format it from ubuntu installer or window disk management? Can't I format it from anywhere i prefer? (I want F to be accessible from both OS BY DEFAULT. I don't want to install some other program to handle this issue)

I suppose so.

> 7. Is Lucid Lynx's manual partitioning same as that of Karmic Koala? (All the videos that i watched to understand manual partitioning were about karmic koala, so it might be difficult for me to install Lucid Lynx if its manual partitioning is any different from karmic koala.)

They are the same.

---

### Post by The Cog on 2010-05-07
1:
No - Ubuntu can happily live completely on logical partitions

2:
Yes - I advise at least 4G for /, maybe 2G for swap, and the rest for /home. Actually, I have two partitions for /, and alternate between them as I install the next version. That way, if an install has problems, the last version is still there.

3:
No need at all.

4:
No need to shrink other partitions, 21G is enough to start trying Ubuntu. Just delete G and then create the other partitions you want.

5:
Ubuntu can read/write NTFS just fine, so no need to re-format F.

6:
Mooted by 5. However if you did re-format it, either OS could do the job.

7:
They are the same - I don't remember any difference.


Make sure you have backups before starting. Mistakes during partitioning can lead to disappointment. You will have to use the live CD or installer CD to create the Ubuntu partitions because Windows can't make ext3/ext4 or linux swap partitions.

Come to think of it, although the installer partitioner hasn't changed, I think the partitioner that you use in the live CD "try without installing" has changed. Previously I used gparted. I can't remember if gparted is there on the live CD anymore, but the really slick Disk Utility seems to have replaced gparted on the real installs.

---

### Post by kio_http on 2010-05-07
Chose well, you may want to try Kubuntu or Xubuntu also.

[SIZE="4"]Screen-shots[/SIZE]

**Ubuntu 10.04 Lucid Lynx (GNOME Desktop Environment)**
[IMG]http://img88.imageshack.us/img88/7215/ubuntudesk.png[/IMG]

**Kubuntu 10.04 Lucid Lynx (K Desktop Environment) **
[IMG]http://img88.imageshack.us/img88/9054/airas.jpg[/IMG]

**Xubuntu 10.04 Lucid Lynx (XFCE Desktop Environment)**
[IMG]http://img215.imageshack.us/img215/4930/defaultyr.png[/IMG]

---

### Post by HDave on 2010-05-07
> **SKhan said:**
> 
My questions are:
1. Is it necessary for ubuntu to be installed on a primary partition?

2. Is 21GB space enough for ubuntu 10.04? Will it effect ubuntu's running speed and performance? (Since My primary OS will still be Windows because other family members who are extreme novice will be using my computer for watching youtube videos. So i am forced to install ubuntu on as less space as possible.)

3. Should I still defragment all the partitions, even if the partition i am going to install ubuntu on is totally empty? (personally i don't see any need for doing so)

4. Should I still shrink one of the partitions? (personally i don't see any need for doing so)

5. I want F: partition to be accessible from both Operating Systems. So should I format it with fat32? Or NTFS still has advantage in this scenario? (i already know fat32 is not a journaling FS. But for a couple of reasons i want to format F: with FAT32)

6: If I format F: with FAT32, is it necessary to format it from ubuntu installer or window disk management? Can't I format it from anywhere i prefer? (I want F to be accessible from both OS BY DEFAULT. I don't want to install some other program to handle this issue)

7. Is Lucid Lynx's manual partitioning same as that of Karmic Koala? (All the videos that i watched to understand manual partitioning were about karmic koala, so it might be difficult for me to install Lucid Lynx if its manual partitioning is any different from karmic koala.)


1. I have not installed it on an extended partition, but I think you'll be fine.  When you run the installer, do not select "automatic" mode -- use "manual" model and pick your partitions.

2. 21 GB is WAY more than you'll ever need.  When I have it fully loaded it barely ever gets to 6GB.

3. No defreg needed.  Interestingly, you find there is no defrag utility for Linux....the filesystems render it unnecessary.  Defrag is a windows only phenom.

4. No.

5. Linux can read/write to every Windows file system type including Fat32 and NTFS....so either way you'll be fine.   You can mount that filesystem automatically if you want by putting an entry in /etc/fstab after you get Ubuntu up and running.  However your Gnome desktop environment will automatically recognize it as a Windows filesystem and put an icon on your desktop.

6. You can format it in either place.  A FAT32 file system is the same whether formatted in windows or linux.  BTW -- I have a dual boot Win/Ubuntu laptop and have shared the same files between both for years.

7. Very much the same...actually has changed much in years.  BTW, if you have enough RAM, you can skip creating a SWAP partition...its optional.

-- Remember to have fun with it and enjoy!

---

### Post by romeug on 2010-05-07
I am fairly recent to this, but did a dual boot restoration of an old laptop after inserting a hard drive with XP and Ubuntu Studio.
I installed XP clean, then did all the manual partitioning in Ubuntu 9.1 and upgraded...

1.My Ubuntu is on a logical partition, though i believe that the Grub is on the primary
2.I believe 21g is more than adequate for the basic install, i would consider a small partition for a swap.  I did 1 gig
3.this was recommended in all my reading, i did not do it on mine as it was a clean install
4.I don't see the necessity for shrinking one, I guess that would have more to do with your data needs.
5.I did my shared disc FAT32 from the results of my research, though i cannot remember the citation
6.I did it with Ubuntu with no problems reflected by Windows, and see no reason that it would not be accommodated in reverse.  I can understand your reservation as Windows 7 is a bit picky about certain things (though quite a bit better than Vista) 
7.Can't answer that, i used 9.10 which went very smoothly.  If you feel more secure, use a karmic install as my upgrade went without a hitch...

I look forward to someone with more expertise to critique the above, by codifying it i am trying to learn myself...

---

### Post by SKhan on 2010-05-07
Thank you guys, you all are so cooperative & so quick to answer my questions. I really relieved me a lot. Now i have gained the courage to install ubuntu tonight.
Again Thank you soooooooooo much.;)

---

### Post by SKhan on 2010-05-07
> **The Cog said:**
> Make sure you have backups before starting. Mistakes during partitioning can lead to disappointment.
Already backed up 3 times. So if something wrong happens, it would only cost me TIME. :p:-&

> **The Cog said:**
> You will have to use the live CD or installer CD to create the Ubuntu partitions because Windows can't make ext3/ext4 or linux swap partitions.
Live CD ready. :-\"

---

### Post by SKhan on 2010-05-07
> **kio_http said:**
> Chose well, you may want to try Kubuntu or Xubuntu also.
of course Kubuntu, when it comes to looks/transparency. But i had made my mind to install ubuntu first & when i get used to linux, i will for sure try other distros as well, specially Kubuntu is on my priority list.

---

### Post by sakisds on 2010-05-07
> **SKhan said:**
> of course Kubuntu, when it comes to looks/transparency. But i had made my mind to install ubuntu first & when i get used to linux, i will for sure try other distros as well, specially Kubuntu is on my priority list.

Kubuntu looks better, but you might find it a bit harder to learn that ubuntu. And since you are a new user, stick to ubuntu for now. ;)

---

### Post by SKhan on 2010-05-07
> **sakisds said:**
> Kubuntu looks better, but you might find it a bit harder to learn that ubuntu. And since you are a new user, stick to ubuntu for now. ;)
that's what i thought.

---

### Post by kio_http on 2010-05-07
> **sakisds said:**
> Kubuntu looks better, but you might find it a bit harder to learn that ubuntu. And since you are a new user, stick to ubuntu for now. ;)

Not anymore. The Kubuntu team worked very hard to make KDE 4.4 a stable, functional and zeroconf DE.

---

### Post by HDave on 2010-05-07
Kubuntu 10.4 is great, but I recommend vanilla Ubuntu with Gnome for new users.

Also here is a tip for sharing a partition between Linux and Windows which you will absolutely run into at some point.

-- I your windows system hands or otherwise is stopped abnormally then you filesystem will be marked as dirty/corrupt/etc.  Windows will remount it fine without complaining, but Linux respects this and will not mount it.

Your choices are to:

1) reboot windows and shutdown normally
2) Use a linux command to reset the flag
3) Mount the filesystem manually with the mount command and use the --force option.

Good luck...

---

### Post by SKhan on 2010-05-09
Thank you guys, ubuntu 10.04 installed successfully on my system, although in 4th attempt. First 3 attemps failed, & i am sure i did no mistake in first 3 attemps. It's working in perfect harmony with windows 7. well almost perfect. ;)
thanks again for your swift co-operation.

---

### Post by SKhan on 2010-05-09
> **kio_http said:**
> Not anymore. The Kubuntu team worked very hard to make KDE 4.4 a stable, functional and zeroconf DE.
kio_http, a good news for you!
i have made my mind to migrate to kubuntu in a week. have download kubuntu-10.04-desktop-i386.iso :P

---

