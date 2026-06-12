---
title: "Installing - multiple disks"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by Steven_S on 2010-03-12
Here I go, and already ran into my first snag :p

I am trying to install Ubuntu next to XP on a desktop. The system has four disks: 

SDA to SDC 1TB storages
SDD: the system disk

Yes, I know, I should have plugged them in differently...

The installer wants to use SDA, but I want to use SDD. I am afraid of the manual method - could someone run me through how to do this? 

SDA is NFTS, but also has a FAT partition (I guess for drivers and the XP rescue disk).

---

### Post by audiomick on 2010-03-12
No need to be afraid of the manual partitioning. It is not that hard, you just need to pay attention to what you are doing.

The graphic installer  on the live CD uses gparted. You need to know about this selector
[ATTACH]149865[/ATTACH]
to select which drive you are working on.

The subject of partitioning is a bit too broad to cover in a few easy sentences. It would be better if you do a bit of reading here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

and maybe this
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Steven_S on 2010-03-12
Thank you very much! Even more reading to do :-). 

While I am partitioning: would you recommend making a separate partition for grub and one for /home?

---

### Post by audiomick on 2010-03-12
> **Steven_S said:**
> Thank you very much! Even more reading to do :-). 

While I am partitioning: would you recommend making a separate partition for grub and one for /home?
Definitely a separate /home. For most "normal" users there is no reason to put any of the other system directories on a separate partition.

I would just let the installer put grub where it wants to. I haven't ever done any different to that. I don't know of any reason, on a "normal" install, to have a separate /boot partition.

---

### Post by steve-shinn on 2010-03-12
You don't need to make a partition for grub, but i would definitely create a partition for home

---

### Post by Steven_S on 2010-03-12
Sorry to expand... how big should the "home" partition be? I plan to put files such as documents on one of the storage disks.

---

### Post by audiomick on 2010-03-12
That is up to you to an extent.
Is use this scheme
10 - 15 GB partition mounted at /
swap = size  of RAM + a little bit
the rest /home

If you do not need the computer to be able to hibernate, about 1GB of swap should be enough, but if you want to hibernate, the swap needs to be as big as the RAM.

I have read hear of one bloke who symlinks everything to storage folders outside of home. He says the his /home is only couple of GB. Given that you have bucket loads of drive space, I don't think you need to be that severe.
How big you make it depends on where you put it. Don't forget, there is nothing that says /home has to be on the same drive as /. Mine isn't:
```
mick@ubuntu-desktop:~$ sudo fdisk -l

Platte /dev/sda: 80.0 GByte, 80026361856 Byte
255 Köpfe, 63 Sektoren/Spuren, 9729 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xc3f8aac4

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            3649        9729    48845632+   5  Erweiterte
/dev/sda3            1825        3648    14651280   83  Linux
/dev/sda5            9328        9729     3229033+  82  Linux Swap / Solaris
/dev/sda6            3649        5593    15623149+  83  Linux
/dev/sda7            5594        9327    29993323+  83  Linux

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x63eba0e6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1       60424   485355748+  83  Linux
/dev/sdb2           60425       60801     3028252+  82  Linux Swap / Solaris

```
sda 1 is the / of the main install, the /home for that is sdb1. Both swap partitions are in use, but I think that the literature that led me to set that up was out of date.

There is also a test system on sda3, a /home for that on sda6, and some "spare" storage space that I rarely use on sda7.


I think you can afford to give your XP lots of room on sdd (how big is that drive?) and make a /home out of what is left of that drive after you have allocated space for / and swap, even if is only 10GB or so, or even think about putting your /home on one of the other drives.

---

### Post by Steven_S on 2010-03-12
The drive is 80GB. I'm pondering to put home on one of the TB drives. Certainly has an advantage for when I want to change the system disk, and as I will have different users on the system...

If I put it on a different drive, do I need to point Ubuntu to that on install?

---

### Post by audiomick on 2010-03-12
It is the same wherever you put it: you need to choose the drive your want to work on, create a partition and specifiy the file system type and mount point.

You don't have to be too nervous about it: the installer doesn't do anything permanent until you tell it to.

You might consider doing a practice run with only "empty" drives connected, and erase it again when you do your "real" install. The time it costs you might be worth it for the peace of mind when you do the install you want to keep.

---

### Post by audiomick on 2010-03-12
Here are my thoughts regarding your PM:

> ... because I have no idea how big FOSS programmes are, and if they require things to be in the same place. For example, I could manage my pictures with F-spot, which then would be running on my system disk but would be using files from one of the storage disks. Can it work that wayLinux / Ubuntu installs programs in various folders in the level below /, for instance in /bin, in /usr/games and other locations. To be quite honest, I don't really know exactly what goes where. I am familiar with the process in windows where one can install a program to a specific location. In fact, it is a very relevant issue with my Vista laptop, which is configured with a C: partition that is so small that I had space problems within 3 weeks of buying it.

Linux is different, and I am not aware if it is even possible to change where programs are installed to. On the other hand, for comparison, the laptop has around 15GB in the part of the drive where the system is, and my Ubuntu machine, with a separate /home partition, has around 6.5GB in the / partition. 

The Ubuntu machine has a lot more programs installed than the Vista Laptop. The laptop has open office, an acoustic analyser and a related acoustic simulator, a handful of programs for Yamaha Digital Audio devices, and that is about it. The Ubuntu machine has everything from a standard install, plus an entire Ubuntu Studio package set, plus anything that has in any way interested me in the last 2 years or so.

As far as where the Data goes, of course there is always the "save as" option to manually specify where the file gets stored. More importantly, I can't recall a program on the Ubuntu machine in which it isn't the easiest thing in the world to change the default store path to something else, i.e. to tell the program where to store to by default. My impression is that this is a lot easier on average than in windows. I can distinctly remember being very annoyed about not being able to change that in various windows programs (whereby that is the fault of the programmer rather than an intrinsic windows problem), and I can't remember not being able to change it for a program on Ubuntu. So yes, it can work in the way you want.

> If I can use software installed on my system disk to handle the files on the other disks (and if they stay there on the other disks), then just a "Normal install" without moving /home or program files would do. As already stated, you can easily handle files on other disks. I would still recommend a separate partition for /home for the sake of being easily able to retain all your user settings and configurations in the event of a fresh install. These things get stored in your /home directory, and I don't think it is sensible or even possible to change that. It is no great effort to set up a partition for /home during the install, and having it can save you a lot of effort in the event that something shoots down your system and you have to re-install it. The programs that you have installed over and above the standard install will have to be re-installed, but once they are back, they will find the config files in the retained /home and be there where they were before the crash.

> I guess that is what is meant by "symlinks". I am afraid I am a bit shaky on symlinks, as I don't use them myself. As I understand it, a symlink is there where the program expects to store to and points on to where you want it to really store to, and vice versa points the program on to read where the file is instead of where it expects it to be. There is a reference in this post about creating them.
[http://ubuntuforums.org/showpost.php?p=8956372&postcount=6](http://ubuntuforums.org/showpost.php?p=8956372&postcount=6)

> Or to refine that into two questions: 
a) does FOSS generally take up less space than Windows software? 

b) if I install things on a separate disk (by putting /usr and /lib elsewhere than the system disk), and I later do a fresh Ubuntu install on the system disk, will the installed software break or still work?I think we have covered both of these.
 In my experience, an Ubuntu install is definitely smaller than a Vista install. An XP install would probably be smaller than an Ubuntu 9.10 install, but I am pretty sure it grows more with time than Ubuntu does. I don't know about win7. I have heard that it is a lot more economical with space than Vista, but I don't know how much.

You could put /usr and /lib and in fact any directory on it's own partition, but I really don't know if that would allow you to retain installed programs. I tend to think not, if only because that would surely completely confuse the package management mechanism. If you were to retain programs from a previous install, I think dpkg/aptitude/synaptic would not know they are there and therefore not keep them updated. 

This thread
[http://ubuntuforums.org/showthread.php?t=1300029](http://ubuntuforums.org/showthread.php?t=1300029)
has some good suggestions about saving a list of what is installed before a re-install and using it to re-create the install afterwards. Particularly interesting are post #10 from Herman and the link in the last post.

I hope that makes things a bit clearer for you.

---

### Post by egalvan on 2010-03-12
> **audiomick said:**
> 

Linux / Ubuntu installs programs in various folders in the level below /, for instance in /bin, in /usr/games and other locations. 

In the *nix-style file systems, everything logically flows from /,
no matter where it is physically.

So putting different system folders (or anything else) on different partitions, or different hard drives, will have no impact on the ability of the system to "find" things it needs.

In days of yore, I roultinely had boot, swap, usr, temp and home all on different partitions... indeed usually on different drives (we called them spindles). 
this was done for performance issues, back when 100M drives were large... and usually SCSI.
Six to ten small drives on at least two SCSI chains...


> I am afraid I am a bit shaky on symlinks, as I don't use them myself.

A link is just a connection between where the file logically lives, and where it physically lives.

It's a pointer, nothing more or less.

It looks (almost) exactly like a regular directory entry.

I could have *myfav.avi*, which is a large video file,
physically on the /home partition,
or I could move that large file to another drive,
and change the *myfav.avi* to a link, which will point, or "link" to the actual location on the other drive.

I could have all my videos in /home/videos,
or I could have them on a seperate, larger, drive,
and make the directory entry a link which points to the actual location.

This is also ideal for when the data is going to be shared by two or more users...
have them all link their /home/video directory to the drive which actually contains the videos, or audio, or docs, etc...

> You could put /usr and /lib and in fact any directory on it's own partition, but I really don't know if that would allow you to retain installed programs. I tend to think not, **if only because that would surely completely confuse the package management mechanism**. If you were to retain programs from a previous install, I think dpkg/aptitude/synaptic would not know they are there and therefore not keep them updated. 


The system would not get "confused" as to** where** /use and /lib, etc are "located".
Again, **logically, they flow from /**.
Where they are **physically **is (almost completely) irrelevant.

One may even have part of the OS on a different networked storage, as long as they get mounted and are available when needed in the boot process...
think "thin clients", which may have NO local hard drives at all...

As far as retaining software between installs, this is not something that location will impact... rather, **it will be impacted by software versions, and installed dependencies, libs, etc. etc.**

---

### Post by audiomick on 2010-03-12
> **egalvan said:**
> 
this was done for performance issues, back when 100M drives were large... and usually SCSI.
Six to ten small drives on at least two SCSI chains...
so you would be over 18 then...;)

> The system would not get "confused" as to** where** /use and /lib, etc are "located".
Again, **logically, they flow from /**.
Where they are **physically **is (almost completely) irrelevant.

One may even have part of the OS on a different networked storage, as long as they get mounted and are available when needed in the boot process...
think "thin clients", which may have NO local hard drives at all...

As far as retaining software between installs, this is not something that location will impact... rather, **it will be impacted by software versions, and installed dependencies, libs, etc. etc.**

That is what I was trying to get at, although I didn't express it as well as that.

Thanks for filling in the gaps.:popcorn:

---

### Post by Steven_S on 2010-03-13
Thank you very much for this information, people. This fills a lot of gaps between "reading up" and actual experience. 

Getting Linux on this box is more a matter of "can do" than of necessity, and Ubuntu would give me a way to do that with a well-thought GUI and to get things up and running. Getting to understand what is behind that, little by little, is a big personal goal for me. I am in the phase of getting to understand what I personally need to know to make informed decisions. The rest will follow, I guess :-). 

The next thing for me to figure out is SAMBA and issues related to that - in order to come to a setup where everything is accessible, and then further down the road start making some folders specific and back up automatically. I have received some good references for that in other posts, so back to reading ;).

---

### Post by egalvan on 2010-03-13
> **audiomick said:**
> so you would be over 18 then...;)

uhmmmmmm, that would be back to nineteen and seven two, there-abouts...
back when "personal computers" were found only in the the halls of science fiction... Asimov, Heinlien, etal.
That *Popular Science* ad was still some five years away!! :)
Which issue I still have, by the way. :KS


> That is what I was trying to get at, although I didn't express it as well as that.

Thanks for filling in the gaps.:popcorn:

Well, I'm not used to my ramblings  being referred to as "well expressed" ! I thank you.

---

