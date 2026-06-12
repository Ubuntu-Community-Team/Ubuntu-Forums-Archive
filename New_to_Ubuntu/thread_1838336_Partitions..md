---
title: "Partitions."
date: 2011-09-03
forum: New to Ubuntu
---

### Post by tylerfly on 2011-09-03
Hi, I'm not entirely new to Ubuntu or computers, and this will be my second time installing it full time on a computer. My reason for installing is that my motherboard messed up and we had it replaced, so I can't use my current Windows Vista OS.

I have two partitions on my hard drive. One has all the backup information from windows, the other has windows itself. What I would like to do is install Ubuntu over Vista and keep my backup partition.

I have several questions, as I am operating on the LiveCD now: If I do this, will the two partitions be able to interact like they did on windows (they behaved like separate HDs in the "My computer" section.) and can I install Ubuntu and keep my information at the same time? If so, how would I go about that? Just through the live installer or some other program? The live installer recognizes my partitions, but there are a few things I just don't understand going on there. 

Thanks in advance :)

---

### Post by Leshrac on 2011-09-03
Yes, you can format the partition where vista is installed as ext4 and install ubuntu in there.

This will not affect the other partition, you will be able to access it in any way you like, but the behaviour you described is the default one in ubuntu.

The installer has some default options that try to automate the process of choosing the partitions. I am not entirely sure about what will these options do to your existing partition setup, so I would use the option to specify the partitions manualy just to make sure nothing is deleted that you don't want to.

EDIT: In any case, specially if you are not very sure about what you are doing, make sure you backup everything you want to save before doing anything.

---

### Post by tylerfly on 2011-09-03
I am unsure how to backup my information because I have been told that I can't use Windows Vista with the new motherboard. I also have no discs for windows vista. can I somehow reach my information and back it up using only the live CD and one DVD drive? I have tried reaching my partitions through the live CD, and it recognizes that they are there (lists them in "places") but when I click on them, it seems to have no effect, nothing happens. 
Thanks again!

---

### Post by grahammechanical on 2011-09-03
Hi welcome to the forums.

I have tried to find a guide that will show you what you will see when you first install Ubuntu. This is what I found.

[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/")

At least you can know in advance what screens you will see.

I have three different versions of Ubuntu installed, each in its own partition (drives in Windows). An installation into one partition does not affect what is on the other partitions unless I make the mistake of telling the installer to format that partition.

I can also access the files on each of these partitions from any of the three Ubuntu installations. Your Windows Backup partition (Drive) will be in a Windows format but Ubuntu will be able to read and write to the drive. So, do not change the format of this back up drive (partition) or you will lose all the data.

May I suggest that from the live CD you run Disk Utility and take a screen shot and post it here. Then someone can offer advice about the partitions you have and how to make use of them.

Regards.

P.S. Some will say (unlike the guide in the link) that a boot partition is not necessary. I do not have one. I have not had any problems.

---

### Post by tylerfly on 2011-09-03
What I am confused about is where to put Ubuntu for now so I can get my music, pictures, etc. off of the backup partition (BILL), then later delete the windows partition (PELICAN) I have included two screenshots, one of when I install Ubuntu and it asks me where to do so, and one of the disk utitlity. I hope this helps. 

Thanks.

---

### Post by coffeecat on 2011-09-03
> **tylerfly said:**
> I have tried reaching my partitions through the live CD, and it recognizes that they are there (lists them in "places") but when I click on them, it seems to have no effect, nothing happens. 
Thanks again!

Did you have one of Gparted, Disk Utility or the installer open when you clicked on the partition in the Places menu? If you have the Gparted partitioner open, you cannot automount a partition from Places. I don't know whether this is so when you have Disk Utility or the installer open, but this is worth checking.

Apart from this a partition should automount and a file browser window open when you click on it in the Places menu. Another reason for this not happening is if the filesystem is damaged. Please open Gparted (System > Administration) and post a screenshot of its window. It is far easier to see what is going on with your partitions that with Disk Utility.

---

### Post by Leshrac on 2011-09-03
You should be able to browse through your partitions from the live-cd environment to back up any data you want to save to an external drive, usb stick, cd burner, dropbox/ubuntu one or whatever it is that you like using for backups.

Judging from the screenshots, the first partition "PQSERVICE" is probably the recovery data for your preinstalled operating system. You can keep it just in case you want to go back to your old OS, but if you are sure you won't go back or that it won't work with the new hardware you can delete to have 30GB extra disk space.

What you should do is first of all make sure that there's nothing you want to keep in the second partition "PELICAN", if there's anything ou want to save copy it over to "BILL" or back it up to an external drive.

Then delete the "PELICAN" partition (and the PQSERVICE partition if you are sure you don't need the windows vista recovery), and tell the installer yo use the empty space to install ubuntu.

If everything works well you should be able to access everything you have in the "BILL" partition.

I'm sort of worried about you not being able to access your partitions from the live cd though, you should be able to, can you elaborate on what's happening?

---

### Post by tylerfly on 2011-09-03
Ok, now I can reach BILL (Information partition) from the hard drive and see all the information, this is because i had the installer open. What i would like to do now is transfer all the information somewhere. I only have one DVD drive, and it is running Ubuntu for me right now. I would still like to have a backup partition on my computer, so I want to keep BILL, but get rid of PELICAN and replace it with Ubuntu, how would I go about doing that?
Thanks for all your help everyone.

---

### Post by tylerfly on 2011-09-03
Also, here's the screen shot of GParted if that helps anyone with my problem.

---

### Post by tylerfly on 2011-09-03
> **Leshrac said:**
> You should be able to browse through your partitions from the live-cd environment to back up any data you want to save to an external drive, usb stick, cd burner, dropbox/ubuntu one or whatever it is that you like using for backups.

Judging from the screenshots, the first partition "PQSERVICE" is probably the recovery data for your preinstalled operating system. You can keep it just in case you want to go back to your old OS, but if you are sure you won't go back or that it won't work with the new hardware you can delete to have 30GB extra disk space.

What you should do is first of all make sure that there's nothing you want to keep in the second partition "PELICAN", if there's anything ou want to save copy it over to "BILL" or back it up to an external drive.

Then delete the "PELICAN" partition (and the PQSERVICE partition if you are sure you don't need the windows vista recovery), and tell the installer yo use the empty space to install ubuntu.

If everything works well you should be able to access everything you have in the "BILL" partition.

I'm sort of worried about you not being able to access your partitions from the live cd though, you should be able to, can you elaborate on what's happening?

Thank you so much! :) I am trying to do this right now, but I am having troubles deleting "Pelican." The right click menu from pelican has delete, but it is unclickable. how do i delete PELICAN and PQSERVICE?

---

### Post by Leshrac on 2011-09-03
> **tylerfly said:**
> Thank you so much! :) I am trying to do this right now, but I am having troubles deleting "Pelican." The right click menu from pelican has delete, but it is unclickable. how do i delete PELICAN and PQSERVICE?
The only reason I can think of is that the partitions might be mounted, Gparted won't allow you to delete mounted partitions.

I would just fire up the installer (the installation process automatically unmounts everything and prevents it from being mounted again), select manual partitioning, then delete both sda1 (PQSERVICE) and sda2 (PELICAN). Then I would create an ext4 partition covering all the empty space left by the deleted partitions except for around 8GB left for a swap partition.

Then I would tell the installer to mount the big partition as / and use the 8GB left as a swap partition.

---

