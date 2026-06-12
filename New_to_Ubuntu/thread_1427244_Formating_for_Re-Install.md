---
title: "Formating for Re-Install"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by flue on 2010-03-11
Ok, this one has been driving me nuts for months.  When you go to re-install or downgrade or what-ever, how do you reformat?  I've found that if I make NO changes to the partitions no formating takes place and the install fails 40%-80% in.  I then usually use XP and slave the drive and kill the partitions or reformat in NTFS and then let Linux re-format in EXT.

Ubuntu 9.04 live CD Gpart would not format my SATA drive (didn't even find the drive)  I don't know if 9.10 would have or not.  Is there something I'm just not getting?  Some step I'm missing to wipe out the partition table so Installation thinks it's a new partition?  Or a way to force it to OVER-WRITE the previous installation?

Thanks.

---

### Post by audiomick on 2010-03-11
Theoretically, the installer will re-format and install over an existing installation. If you are having trouble achieving this, then something might be going wrong.

Here are a couple of thought that _might_ be relevant.
As far as I know, the graphic installer has trouble if you don't have much RAM. I think 512MB is the recommended minimum. The alternate CD, which is a text based installer, might work better.

With 9.10, some people have reported that the installer can't find their drive(s). I don't know if this also applies to 9.04. I had the problem with 9.10. I have two drives, and the installer couldn't see one of them. I was able to install using the alternate CD. From what I have seen in the forum, this also worked for a lot of other people with this problem.

You could try using the gparted live CD
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
 to "pre-format" your drive, however I don't know for sure if you will have more luck with that than the live CD, and don't know if doing that would help the installer to find the drive. I tend to doubt the latter.

As far as "force it to overwrite" goes, if you choose the "manual" option at the partitioning stage of the installation, it should do completely and exclusively exactly what you tell it to, which amounts to the same thing.

---

### Post by philinux on 2010-03-11
I have /home on it's own partition. When I reinstall I always edit the / partition, set it to ext4 and mark it for formatting.

I edit the /home partition to set the mount point and the file system but obviously I do not mark it for formatting.

This has never failed. I dont pre format /.

---

### Post by akand074 on 2010-03-11
Like the above poster was referring too, did you mark it for formatting in Gparted during the installation? It should delete everything on the drive, reformat it, and then install the new installation

---

### Post by flue on 2010-03-11
philinus-  I don't know if there is something in the cool-aid I've been drinking but I am just not following what you said.

---

### Post by philinux on 2010-03-11
> **flue said:**
> philinus-  I don't know if there is something in the cool-aid I've been drinking but I am just not following what you said.

Perhaps I should have said I always use manual partitioning. Then you get the options to change the partitions. i.e. specify mount points and wether to format or not.

You can see similar screenshots of what I mean here.

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by flue on 2010-03-11
Thanks.  I'll give it a shot tonight.  I'm thinking I want to go back to 9.10 .  9.04 is missing stuff that I enjoy in 9.10 

I could SWEAR I tell it to format...but maybe I'm missing that tick mark and just setting the partition sizes.  I use manual as well.  Am I better off using EXT4 with 9.10?  Should I not install anything from 9.04 on 9.10 (like Pidgion?) If I download 9.10 again will it have updates already present (Are there updates in a March download that were not present in a December download?) or does it not work like that?

---

### Post by philinux on 2010-03-11
> **flue said:**
> Thanks.  I'll give it a shot tonight.  I'm thinking I want to go back to 9.10 .  9.04 is missing stuff that I enjoy in 9.10 

I could SWEAR I tell it to format...but maybe I'm missing that tick mark and just setting the partition sizes.  I use manual as well.  Am I better off using EXT4 with 9.10?  Should I not install anything from 9.04 on 9.10 (like Pidgion?) If I download 9.10 again will it have updates already present (Are there updates in a March download that were not present in a December download?) or does it not work like that?

Ext4 is the better choice. It is the default in 9.10 and for future releases. 

The current download from ubuntu will have all the updates since December.

However I reckon the downloads are not as big as a downloading a current livecd. Your choice there. 

I would use the packages associated with the release.

---

### Post by flue on 2010-03-11
Thanks, we'll see how things go this evening.  Back to one of your earlier posts.  When install were you installing to /home or /?  When you set ext4 you set the mount point to / correct?  What's the advantage to installing to /home if that's what I am reading?

---

### Post by philinux on 2010-03-11
> **flue said:**
> Thanks, we'll see how things go this evening.  Back to one of your earlier posts.  When install were you installing to /home or /?  When you set ext4 you set the mount point to / correct?  What's the advantage to installing to /home if that's what I am reading?

When reinstalling from the livecd and choosing manual partition the mount points need specifying for each partition and the installer needs to know what file system is in use so it can set up fstab correctly. I always format / (root).

The advantage of /home on it's own partition is that you can reinstall and NOT format the partition. Therefore all application configs, desktop customisations and any data files remain intact. As do firefox profile etc etc.

Here's a screenshot of my partitions.

---

### Post by flue on 2010-03-11
If I'm understanding what your doing here, it's kind of what I do in Windows.  Install the OS on it's own partition and install all programs on another partition.  I'm guess that unlike Windows, Linux allows you to install and re-install the kernel with out messing with the programs on the /home partition.  

Then if you have any problems (failed boot, failed child mounting (forgot the correct wording of that one)) you can re-install the kernel on / and it incorporates the /home and you lose virtually nothing?  

I think I shall do this when I get home.

---

### Post by philinux on 2010-03-11
All you then have to do is reinstall any non-default programmes. They then pick up the config files previously created by them in /home.

I've even gone 32 bit > 64 bit >32 bit and finally settled on 64.

---

### Post by audiomick on 2010-03-11
> **flue said:**
> If I'm understanding what your doing here, it's kind of what I do in Windows.  Install the OS on it's own partition and[COLOR=Red] install all programs on another partition[/COLOR].  I'm guess that unlike Windows, Linux allows you to install and re-install the kernel [COLOR=Red]with out messing with the programs on the /home partition.  [/COLOR]

Then if you have any problems (failed boot, failed child mounting (forgot the correct wording of that one)) you can re-install the kernel on / and it incorporates the /home and you lose virtually nothing?  

I think I shall do this when I get home.
Nearly, but not quite...

First of all, the directory /home always exists. It can be on a separate partition, as can any directory in the file system, but it doesn't have to be. For most desktop users, there is no advantage in having a separate partition for any directory except /home. 

Linux installs programs in various directories, _not_ including /home. The advantage of the separate /home is that (by default) all your data and things like user settings get stored in /home (unless you have stored your data elsewhere). If you re-mount the /home partition as philinux has suggested, your data will still be there in the new install, and practically all of your user settings will still be in place.

If you have installed any programs in addition to the ones that are included in the standard install, you will have to re-install them after a fresh install. Once they are re-installed, they will generally find the appropriate user settings if you have retained an existing /home partition. I have my machine set up with a separate /home partition, and it has saved me a lot of effort re-creating settings and configurations.

If you want to retain a /home directory out of a working installation, I think the link to psychocats that philinux posted has directions for creating a separate /home partition on an existing install. There is also information here
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you don't have an existing /home directory you want to keep, just choose the manual partitioning option during the install, as philinux suggested, and create the following
a partition about 10 - 15GB and mount it at / 
a swap partition a bit bigger than your RAM, if you want the Hibernate function to work. If you don't want to be able to hibernate, about 1GB should be enough.
a partition with the rest of your drive space mounted at /home

I also agree that ext4 is your best choice for a file system.

[]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by flue on 2010-03-11
Ok. Thanks.  That makes sense.  I wasn't quite sure how the whole program thing would work, but saving the settings for those programs still makes a world of difference when your looking at re-installing.

---

