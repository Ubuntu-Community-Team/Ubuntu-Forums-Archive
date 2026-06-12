---
title: "Sharing partitions between linux distros"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by SwatKat on 2009-12-05
[SIZE=2]Hi

I am trying to multiboot  ubuntu and mandriva with a provision to add more distros. I would like them to share swap space and also data (like a few documents and media files) to avoid duplication of data. But I read that making them share a /home partition is not a good idea since one is gnome and the other is kde. So is there a way to create a separate partition to hold data that is accessible to all the linux distributions? Would accessing it be very complicated? I have just begun to explore linux, but I'm prepared to learn.

I have 100 gb of unpartitioned space in my hard disk ( currently runing win xp). I plan to allocate 25 gb each to ubuntu and mandriva ( /, and /home included) and create a shared swap partition of about 3 gb( I have a 2gb RAM) and a shared data partition of about 15 gb and leave the rest unpartitioned for the other distros that I might add in the future. My last experince with partitioning was disastrous. Ubuntu resized all partitions when I chose the option  to install the OSes side by side. So I'd be very grateful if someone could guide me as to what kind of partitions I should create ( using gparted in ubuntu live cd) and how to set mount points. Any links to tutorials or guides would also be much appreciated. Thanks:)



PS  :Is 25 gb too much or too less space for someone just trying to understand the distro? I will be downloading a lot of applications. So, how much space do you suggest I allocate to / and /home partitions since I wont store much data in my /home folder?[/SIZE]

---

### Post by JoePublic9 on 2009-12-06
Hi SwatKat,
  First I should say that although I having been running linux for about a year now I am still a noob. Having said that, I can honestly say that I have some experience here.
  I have had WinXP on my machine in the beginning but I have since ditched it and run 2 linux distro's now, Ubuntu and Arch.
 As for partitioning your drive there are limits to how many partitions you can have on one drive. I think it's 3 logical and one extended and different combo's but I am not positive. I have 3 logical and one extended partition on my drive so I know that works. I also share the swap partition between distro's. My main OS is Ubuntu but I fool around in and use Arch a lot. Anyway, I use my extended partition for arch making a / (root) and /home. You do not want to share /home directories. You can, however format a partition to a linux file system and share it between distro's. Your partition plan looks good. Setting mount points is easy in Gparted. I have / (root), /home and swap partitions for each distro, sharing the swap of course.
 25 gig is way plenty to run the distro. I just did a fresh install about a week ago with Ubuntu and after adding a bunch of apps I think I am at 6 gig now. That may double pretty fast and triple over very much time but I can't imagine going over my 35 gig partition. Your mileage may vary. esp. if you do video editing etc.
  My biggest advice is back up your important data! In order to get Gparted, file systems and mount points I had to format many times. For me, hands on learning really worked  *wink*
 As far as tutorials and help pages, this is the place to start. And always remember Google is your friend.

 This whole past year has been a great experience for me. I learned a lot and it was fun. The Linux/Ubuntu community is the absolute best.
   Good luck,
     Joe

---

### Post by iamgeniusrnti on 2009-12-06
Attached you will find my gparted snapshot.  I have a d250 netbook.  On partition 1 is my standard Xp rescue partition.  Probably should have deleted it but oh well.  Part 2 is my XP.  Part 3 is my Ubuntu UNR.  Part 4 extends to part 5 is a NTFS partition visible to ALL OSs.  Part 6 is my Kubuntu NBR.  Part 7 is my Swap which is visible to ALL LINUX OSs.  Part 8 is my Puppy linux... Not sure why I have it--it sounded cool.

---

### Post by coffeecat on 2009-12-06
> **SwatKat said:**
> [SIZE=2]But I read that making them share a /home partition is not a good idea since one is gnome and the other is kde.[/SIZE][SIZE=2]
That's not really a problem since KDE and gnome use different hidden configuration folders. But with Ubuntu and Mandriva, there is one big problem, unless you take great care to set up your user accounts manually. The first created user has a UID of 1000 in Ubuntu, but 500 in Mandriva. You will run into permission problems if you have a shared /home. As a general rule, the last time I checked, the first-created user has a UID=1000 in the Debian-based distros and in openSUSE. UID=500 in the RPM distros Fedora, Mandriva and PCLinuxOS.

[/SIZE]> **SwatKat said:**
> [SIZE=2]So is there a way to create a separate partition to hold data that is accessible to all the linux distributions? Would accessing it be very complicated? I have just begun to explore linux, but I'm prepared to learn.[/SIZE][SIZE=2]
So long as you keep Windows on that machine, why not have a separate data partition formatted NTFS? Ubuntu and most other Linux distros read/write NTFS quite reliably and, being a MS filesystem that doesn't support Unix/Linux permission, you'll neatly get around the permissions problem I describe. This way, you'll have a data partition accessible from each Linux distro as well as Windows. But only do this if you keep Windows. In the rare event of getting filesystem corruption, you'll need a Windows chkdsk to repair it.

[/SIZE]> **SwatKat said:**
> [SIZE=2]I have 100 gb of unpartitioned space in my hard disk ( currently runing win xp). I plan to allocate 25 gb each to ubuntu and mandriva ( /, and /home included) and create a shared swap partition of about 3 gb( I have a 2gb RAM) and a shared data partition of about 15 gb and leave the rest unpartitioned for the other distros that I might add in the future. My last experince with partitioning was disastrous. Ubuntu resized all partitions when I chose the option  to install the OSes side by side. So I'd be very grateful if someone could guide me as to what kind of partitions I should create ( using gparted in ubuntu live cd) and how to set mount points. Any links to tutorials or guides would also be much appreciated.[/SIZE][SIZE=2]
You could use the Ubuntu live CD to set up your partitions and then, when installing, select the 'manual' (advanced) option instead of the guided options. Setting the mountpoints is quite straightforward in that. The Mandriva installer/partitioner is somewhat different but effective, but take care. I managed to reformat a 100GB NTFS data partition during a Mandriva install. Entirely my own fault, partly caused by unfamiliarity with the Mandriva installer and not reading the warning messages. Fortunately, all the data was backed up and easily restored.

[/SIZE]> **SwatKat said:**
> [SIZE=2]PS  :Is 25 gb too much or too less space for someone just trying to understand the distro? I will be downloading a lot of applications. So, how much space do you suggest I allocate to / and /home partitions since I wont store much data in my /home folder?[/SIZE][SIZE=2]
Personally, I would make my root partitions smaller if I was using a separate data or home partition. A default install of Ubuntu takes up only about 2.3GB. Even with several extra apps installed I've rarely gone above 5-8GB on my root partition. Make your root partitions - say - 15GB and you've got that much extra for a data partition. Unless you want to run Windows games in wine, that is. You'll need plenty of space in the root partition if you do.

> **JoePublic9 said:**
> As for partitioning your drive there are limits to how many partitions you can have on one drive. I think it's 3 logical and one extended and different combo's but I am not positive. I have 3 logical and one extended partition on my drive so I know that works. I also share the swap partition between distro's.

Let me help you out here. :) With a msdos partition table (which is what standard PCs use) there is a limit of 4 **primary** partitions. To get round this limitation, you can have one, but one only, extended partition in place of a primary. Or you can have one extended without any primaries. You do not use an extended partition directly - it's simply a 'container' for a number of logical partitions. I can't remember the limit for logicals - at least 20 I believe.

The Linux way of numbering partitions tells you what they are:

sda1, sda2, sda3 or sda4 are either primary or extended.

sda5 and upwards are logicals.

[/SIZE]

---

### Post by SwatKat on 2009-12-06
> **coffeecat said:**
> [SIZE=2]
[/SIZE][SIZE=2]
So long as you keep Windows on that machine, why not have a separate data partition formatted NTFS? Ubuntu and most other Linux distros read/write NTFS quite reliably and, being a MS filesystem that doesn't support Unix/Linux permission, you'll neatly get around the permissions problem I describe. This way, you'll have a data partition accessible from each Linux distro as well as Windows. But only do this if you keep Windows. In the rare event of getting filesystem corruption, you'll need a Windows chkdsk to repair it.
[/SIZE][SIZE=2]
[/SIZE]

Thanks:). I could do that. But, since I share a pc with a sibling , I am concerned about how easily this shared partition is accessible through windows. Is it possible to give it some sort of password protection? If not, I'd rather have a data partition that only Linux can access. Then what format would this have to be?

@JoePublic9 and iamgeniusrnti, Thanks a lot:).

---

### Post by Paqman on 2009-12-06
There's no problem with sharing a /home between distros, i've done it for years. Just create separate accounts on the different systems and all the config files will be kept separate.

---

### Post by bodhi.zazen on 2009-12-06
> **SwatKat said:**
> [SIZE=2]I am trying to multiboot  ubuntu and mandriva with a provision to add more distros. I would like them to share swap space and also data (like a few documents and media files) to avoid duplication of data. But I read that making them share a /home partition is not a good idea since one is gnome and the other is kde. So is there a way to create a separate partition to hold data that is accessible to all the linux distributions? Would accessing it be very complicated? I have just begun to explore linux, but I'm prepared to learn.[/SIZE]

First, just as nettiquette, please use the default font size when posting. If you have problems seeing the font, change the settings in your browser ;)

The only potential problem with sharing a swap partition is that each distro tends to format the swap space. This causes the UUID of the swap space to change, so you need to edit /etc/fstab and either mount by dev (/dev/sdxy) or update the uuid.

To see your partitions by uuid , 

```
sudo blkid
```

The only problem with a shared data partitions is Linux permissions. The first user on Ubuntu is often uid = 1,000, but in say Fedora the first user is uid 500, so I do shares by group. You can have the shared partition owned by say root.users with permissions of 770.

Or you can mount the share at /home and use unique user names, but you will still have potential problems with permissions.

> **Paqman said:**
> There's no problem with sharing a /home between distros, i've done it for years. Just create separate accounts on the different systems and all the config files will be kept separate.

Exactly, sharing a /home partition is fine so long as each distro has a unique user. Most often people seem to want to share a /home with the same user name across distros and this will cause conflicts, either because some systems the first user is uid=1000, and with others uid=500, or because of potential conflicts in . (dot) or config files.

---

### Post by SwatKat on 2009-12-07
> **bodhi.zazen said:**
> First, just as nettiquette, please use the default font size when posting. If you have problems seeing the font, change the settings in your browser ;)



Sir, Yessir!!:)
> **bodhi.zazen said:**
>  The only potential problem with sharing a swap partition is that each distro tends to format the swap space. This causes the UUID of the swap space to change, so you need to edit /etc/fstab and either mount by dev (/dev/sdxy) or update the uuid
How do I update swap uuid?


So, I just want to make sure that I have got this right. Please correct me if I'm wrong.
I want to 
# Share data across distros( Suppose I download a cool wallpaper in Ubuntu and I store it in the shared partition I have to be able to use it in Mandriva)

I can
1> Make a shared data partition formatted as linux(?) and to avoid potential permission problems, have the same root user names and set common root UIDs (like 770)while installing all distros( Can that be done?).
OR
2>Have unique user (root?) names in all distros and share a /home folder.

---

### Post by Paqman on 2009-12-07
> **SwatKat said:**
> Sir, Yessir!!:)

How do I update swap uuid?


You'd need to update the UUID refring to the swap file in /etc/fstab. To list the UUIDs:
```
sudo blkid
```
(On non-Ubuntu distros leave off the sudo and instead log into a root shell)
Then paste the UUID into fstab, which you can open for editing with the following command:
```
sudo nano /etc/fstab
```


> I can
1> Make a shared data partition formatted as linux(?) and to avoid potential permission problems, have the same root user names and set common root UIDs (like 770)while installing all distros( Can that be done?).

Since you'll have _different_ user names on the different distros, you can guarantee access by assigning the users to a group with the same group id, then  giving that group access to all the files. Having groups with the same id on different distros doesn't create the same mess having users with the same id does.

> 
OR
2>Have unique user (root?) names in all distros and share a /home folder.

You can do this, but you'd still need to think about where to put your data, and how to give everyone access. You could have both a shared data partition and a shared /home if you want. Besides data, /home contains a lot of other good stuff, like all the user's settings for the software and desktop.

---

### Post by SwatKat on 2009-12-07
> **Paqman said:**
> You'd need to update the UUID refring to the swap file in /etc/fstab. To list the UUIDs:
```
sudo blkid
```(On non-Ubuntu distros leave off the sudo and instead log into a root shell)
Then paste the UUID into fstab, which you can open for editing with the following command:
```
sudo nano /etc/fstab
```

Since you'll have _different_ user names on the different distros, you can guarantee access by assigning the users to a group with the same group id, then  giving that group access to all the files. Having groups with the same id on different distros doesn't create the same mess having users with the same id does.

You can do this, but you'd still need to think about where to put your data, and how to give everyone access. You could have both a shared data partition and a shared /home if you want. Besides data, /home contains a lot of other good stuff, like all the user's settings for the software and desktop.

Thanks. That cleared everything up nicely:).

---

