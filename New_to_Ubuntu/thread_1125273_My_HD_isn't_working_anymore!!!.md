---
title: "My HD isn't working anymore!!!"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by card_ace on 2009-04-14
i have a Western Digital 250 GB external USB HDD.  and suddenly it won't work anymore.  ok that's not entirely true.  it works perfectly in ubuntu.  but it won't work at all in windows, which is all my school has and i need it to work on almost everything.  it happened when it failed to safely eject when the class ended and i had to just pull it and go.  the only thing i can think of it to copy everything over in ubuntu and then reformat the drive.  are there any easier ways?  i don't have 200 gigs of free space to use at the moment, so another suggestion would be great.

---

### Post by LowSky on 2009-04-14
boot into ubuntu, mount the drive, unmount the drive, then boot into windows. it should work, usually the issue is the reverse, with ubuntu not being able to read the drive after a bad windowd unmount.

---

### Post by BDNiner on 2009-04-14
Did it fail to safely eject in windows. I would connect it back to windows and see if disk management can find the drive. Is it being detected at all in windows? I would suggest finding a way to backup your data before attempting anything.

---

### Post by steve101101 on 2009-04-14
if you have that available space on another drive I would most definitely just move the drive's contents over and reformat so the drive will not act up later on down the road. You can move the contents over such as in the middle of the night so that it is not much of an inconvenience to you the user.

---

### Post by card_ace on 2009-04-14
> **BDNiner said:**
> Did it fail to safely eject in windows. I would connect it back to windows and see if disk management can find the drive. Is it being detected at all in windows? I would suggest finding a way to backup your data before attempting anything.

when the HDD is plugged in in windows i can't even get into disk management.  it refuses to load.  just comes up with the hourglass and sits there and waits.
i'll try mounting and unmounting later today and get back when i can.
and steve: i don't have another drive.  the one in my computer is only 40 gigs.  old pc i haven't been able to upgrade.  looks like it might be time for me to go buy that terabyte drive i was wanting

---

### Post by steve101101 on 2009-04-14
if mounting and unmounting in ubuntu doesn't work you can always try to see if the partition table is messed up or completely rebuild it with TestDisk. Here is its wiki: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by halitech on 2009-04-14
in ubuntu, open a terminal and run
```
sudo fdisk -l
``` and check and see what the format is on the drive. If it says Linux, unless you have a driver for ext3 on the windows machine, its not going to be able to read it.

---

### Post by steve101101 on 2009-04-14
> **halitech said:**
> in ubuntu, open a terminal and run
```
sudo fdisk -l
``` and check and see what the format is on the drive. If it says Linux, unless you have a driver for ext3 on the windows machine, its not going to be able to read it.

it sounds like from the prior posts that he used to be able to mount it from a windows school computer meaning it has to be NTFS, FAT, FAT32, etc. and not a linux one such as ext3/4

---

### Post by halitech on 2009-04-14
I would agree but just want the OP to confirm that info in case he was trying to use the ext3 tool in windows. Just seems odd that Ubuntu can still read it but windows cant if it is in fat/ntfs format.

---

### Post by card_ace on 2009-04-14
its formatted in ntfs.  it used to work before, but when i pulled it out of the windows machine without safely ejecting it that's when i started having problems.  and i just tried the mount/unmount suggestion and that didn't work.  it won't read the drive in windows.

---

### Post by LowSky on 2009-04-14
Its very odd that the drive work in Ubuntu and not windows.
 could you show us the terminal result of the command ```
sudo fdisk -l
```

---

### Post by steve101101 on 2009-04-14
im not sure exactly whats wrong with it since Ubuntu can still read the disk. I guess Ubuntu is just that awesome. After typing that in you should get something like this for your disk. Remember it must be plugged in when you do this ...

```

steven@steven-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72479f1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59578   478560253+  83  Linux
/dev/sda2           59579       60801     9823747+   5  Extended
/dev/sda5           59579       60801     9823716   82  Linux swap / Solaris

```

---

### Post by card_ace on 2009-04-14
```
carlton@carlton-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19798   159027403+   7  HPFS/NTFS
/dev/sdb2           23787       30401    53134987+   f  W95 Ext'd (LBA)
/dev/sdb3   *       19799       23786    32033610   83  Linux
/dev/sdb5           23787       29622    46869637+   7  HPFS/NTFS
/dev/sdb6           29623       30401     6257286   82  Linux swap / Solaris

Partition table entries are not in disk order
carlton@carlton-desktop:~$
```

sdb1 is my main partition and sdb5 is a partition that just has movies on it, both usually show up no problem

---

### Post by steve101101 on 2009-04-14
partition table entries are not in disk order isn't really an error but you can fix that here ...

[http://ubuntuforums.org/archive/index.php/t-108649.html](http://ubuntuforums.org/archive/index.php/t-108649.html)

---

### Post by card_ace on 2009-04-14
> **steve101101 said:**
> partition table entries are not in disk order isn't really an error but you can fix that here ...

[http://ubuntuforums.org/archive/index.php/t-108649.html](http://ubuntuforums.org/archive/index.php/t-108649.html)

so that shouldn't be the problem right?

---

### Post by card_ace on 2009-04-15
> **steve101101 said:**
> if mounting and unmounting in ubuntu doesn't work you can always try to see if the partition table is messed up or completely rebuild it with TestDisk. Here is its wiki: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

alright i downloaded and ran this program in windows and it said the structure on all of my partitions was "ok"

i failed to mention this before but my ubuntu linux is installed on my external.  i don't know if that could change how people are thinking but i figured i'd throw that out there.

---

### Post by card_ace on 2009-04-21
well everyone kinda just disappeared on me.  does that mean there's no other suggestions?  anybody?

---

### Post by halitech on 2009-04-21
> **card_ace said:**
> i failed to mention this before but my ubuntu linux is installed on my external.  i don't know if that could change how people are thinking but i figured i'd throw that out there.

that is most certainly going to change things. 

Either boot into Ubuntu, and post the output of ```
sudo fdisk -l
``` or run Partition Editor and post a screen shot of what it sees when looking at the external drive.

is Ubuntu the only thing on that drive?

---

### Post by card_ace on 2009-04-21
> **halitech said:**
> that is most certainly going to change things. 

Either boot into Ubuntu, and post the output of ```
sudo fdisk -l
``` or run Partition Editor and post a screen shot of what it sees when looking at the external drive.

is Ubuntu the only thing on that drive?

i already posted that about 5 posts ago.  3rd post on the second page.
and no, there is about a 30 gig partition of ubuntu formatted with ext3, a 150 gig partition of stuff formatted with NTFS, and a 50 gig partition with movies formatted with NTFS, along with a 6 gig swap partition.  these numbers aren't exact as its been a while since i formatted the drive, but they should be fairly close.

---

### Post by halitech on 2009-04-21
sorry, didn't clue in on the info

so you have an internal drive with windows that boots fine. You have the 250gig external that boots Ubuntu fine. is grub installed on the MBR of the internal drive or the external? Does Ubuntu see all of the partitions in Nautilus? (just checking cause you mentioned usually works in another post)

If Ubuntu sees everything and windows can't, then something is screwy with the NTFS formating and there may not be any other resolution then formating. Not sure it would effect it but is there any free space on the external in the NTFS partitions?

---

### Post by card_ace on 2009-04-21
grub is on the external drive. i did that so i could boot into linux on computers other than just my home one.  ubuntu can see all my partitions no matter what computer i boot into, and no matter what windows computer i plug the HDD into it doesn't work.  There's not a whole lot of free space on the NTFS partitions.  probably about 5 gigs between the two.  when i said it usually worked in linux, the only reason it didn't work is because i forget to safely remove hardware sometimes.  but i'd just boot into windows and eject it and it worked fine.

---

### Post by halitech on 2009-04-21
ok, only thing I can think of is if copying files to the NTFS partition from Ubuntu may have corrupted the filesystem to where windows can't read it. Other then a format I'm out of ideas on things that may help.

---

### Post by card_ace on 2009-04-21
yeah me too unfortunately.  my buddy has a terabyte external so i think i'm gonna borrow it over the weekend and fix this finally.  any suggestions are still welcome of course :)

---

