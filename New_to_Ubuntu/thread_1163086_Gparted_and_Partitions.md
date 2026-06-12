---
title: "Gparted and Partitions"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by daveedking on 2009-05-18
I like Ubuntu better than windows.... i want 2 remove all Vista from my internal hard drive...actually another reason is because windows wont boot now im sure i messed up some where but Ubuntu is great ..just got it and i like it so how do i wipe out windows?
[B]XXX
_[IMG]http://i713.photobucket.com/albums/ww140/daveedking/help-partitions.png[/IMG]_
XXX
i started out originally with  two 111gig hard drives C: and D:  ... i just want ubuntu.....I  dont care about vista..
  I'm New 2 Linux so keep it Simple please..ThanX...zDA-VeeD
[/B]

---

### Post by Sidewinder1 on 2009-05-18
Just reformat sda1, sda2, and sda3 from ntfs to ext3; provided that you're willing to loose _**all data**_ and programs on those partitions. You may wish to do some searching for different partitioning schemes and separate *home* partitions, etc., prior to doing anything else.

---

### Post by Gone fishing on 2009-05-18
Looks a little odd to me I take it the NTFS partitions are all vista and other windows stuff. You could delete the partitions using gparted but this will probably leave you having to fix grub as your root partition wont be /dev/sda7. So you could reformat the ntfs partitions as ext3 and mount them as home2 or something. However the 2 swap files is also odd and the little ext3 partition?

I think back up all my personal files delete all the partitions and re install Ubuntu with a root / and a home partition /home possibly run Windows in virtual box for the odd time its needed.

---

### Post by Sidewinder1 on 2009-05-18
I was just reading this thread:
[http://ubuntuforums.org/showthread.php?t=1159701](http://ubuntuforums.org/showthread.php?t=1159701)
With all due respect, you may wish to dual boot for a while longer. No sense burning your bridges behind you until you're absolutely certain.

{Sidewinder ducks as ubuntu fans attempt to pelt him with rotten tomatoes and rotten eggs}
:-)
Side

---

### Post by GOfree on 2009-05-18
Great colour scheme, Sidewinder1! I really like it. :)

How about this... 1) make your second hard drive a data drive, and 2) break up your first hard drive into four partitions for three OSes and a swap.

On the first hard drive, you could have one (or two) version(s) of Ubuntu, Windows XP (if you like), and some other distro that you feel like mucking about with (Arch Linux is great, or maybe some new release of Ubuntu that you want to test out first) -- two solid OSes, plus an "experimental" one. You have tons of room (111 GB) for three plus swap.

Then your second drive can be pure storage that all three can access. (Kinda like a separate /home partition, but /home contains configuration data that should stay with each OS.) I haven't tried doing this with Windows, but it sounds like you had it set up like this (C: , D: ) before anyways, so you already know how. 

Ubuntu does not take up much room on your hard drive. :) You might as well put a couple of other distros on while your at it.

---

### Post by NHArticleTen on 2009-05-18
> **Sidewinder1 said:**
> I was just reading this thread:
[http://ubuntuforums.org/showthread.php?t=1159701](http://ubuntuforums.org/showthread.php?t=1159701)
With all due respect, you may wish to dual boot for a while longer. No sense burning your bridges behind you until you're absolutely certain.

{Sidewinder ducks as ubuntu fans attempt to pelt him with rotten tomatoes and rotten eggs}
:-)
Side

Seconded

---

### Post by daveedking on 2009-05-18
> **Gone fishing said:**
> Looks a little odd to me I take it the NTFS partitions are all vista and other windows stuff. You could delete the partitions using gparted but this will probably leave you having to fix grub as your root partition wont be /dev/sda7. So you could reformat the ntfs partitions as ext3 and mount them as home2 or something. However the 2 swap files is also odd and the little ext3 partition?

I think back up all my personal files delete all the partitions and re install Ubuntu with a root / and a home partition /home possibly run Windows in virtual box for the odd time its needed.

If u mean the partition scheme here looks off.its because it is..This is what happened//
 as i was installing Ubuntu i had a big problem with partition and size i feel some how i wrote over windows and messed it up..i cant boot into windowz... i get an error ( Cannot find file C:\d2d\images\*.WSI when trying to determin the UI Language) is if i try booting with mt acer E-Recovery disc i get this error (Restore Failed-reaon 0x90000001..)
so i called acer they said because i dont have the actual vista disc and i just have the E-recovery that i would have 2 pay for that disc..so ....i just kept looking around and reading and found G-Partion tool here so ..Forget Windowz.. i want my 225 gig of linux...so whats the best action ??? And couldn't i just use 
GParted  to custimize the partitions again in the future?|?

---

### Post by daveedking on 2009-05-18
> **Sidewinder1 said:**
> Just reformat sda1, sda2, and sda3 from ntfs to ext3; provided that you're willing to loose _**all data**_ and programs on those partitions. You may wish to do some searching for different partitioning schemes and separate *home* partitions, etc., prior to doing anything else.

ok i did it this way:
[B]XXX
[IMG]http://i713.photobucket.com/albums/ww140/daveedking/patition_2.png[/IMG]
XXX
can i merge sda 1 sda 2 sda 3 to just say sda not in three parts?
and the other partions what do tyhe mean??
(DA-VeeD) And tha devisda7 7 and 8 are those the miss formated partitions ?
[/B]

---

### Post by daveedking on 2009-05-18
[IMG]http://i713.photobucket.com/albums/ww140/daveedking/patition3.png[/IMG]
Is this all ..im are running on sda7??

---

### Post by NightwishFan on 2009-05-18
Perhaps.. You should use the beginning of your drive as a data or backup partition. Here is my setup:

```
sda1|type:ext3|size:120gb|mounted: /mnt/backup
sda5(extended)|type:ext3|size:200mb|mounted: /boot
sda6(extended)|type:swap|size:1.4gb|mounted: SWAP
sda7(extended)|type:xfs|size:70gb|mounted: /
```

Back up your personal data to the large sda1 partition, and then reinstall Ubuntu, and use 'manual' as the setup. Configure Ubuntu to have a swap size about 1.5x your RAM and the remaining space as a root ext3 partition (mount point: /). Tell the installer to use the backup partition as ext3, do not format and mount it as /mnt/backup.

```
sda1 ext3 noformat /mnt/backup
sda2 swap
sda3 ext3 format /
```

---

