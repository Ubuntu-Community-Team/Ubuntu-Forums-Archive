---
title: "Dual Booting and Partitioning"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by canac on 2010-06-04
I should mention first that I'm new to this, but I have spent some time researching the issue. However, I can't quite seem to find the information I'm looking for.

I would like to dual boot Windows 7 x32 and Ubuntu 10.04. I've managed to successfully do this, but I would like to make sure I do it in a way that's "good" and generally makes sense. The trouble I'm having is that a lot of the information out there seems to be outdated, particularly with respect to hard drive partitioning. For instance, [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) seems to indicate, with the statement, "[this tutorial's] general guidelines and principles are still valid, but at this point in computing history, I think the idea of a traditional dual-boot with separate partitions for each OS and then a possible shared partition is a bit antiquated," that partitioning or the traditional idea of partitioning is now obsolete.

If this is the case, then what's taken its (separate partitions for each OS and data) place? As a relatively new (to Ubuntu) user and starting with a clean drive, how should I go about partitioning or not partitioning my drive during installation?

For what it's worth, just for experimentation, I installed the dual boot two ways. First, by installing Windows and then shrinking the partition in Windows, and then installing Ubuntu on the unallocated space. Then, thinking it would be smart to have a separate data partition, I formatted, used GParted running off the CD to create my 3 partitions, then installed Windows, followed by Ubuntu.

I've been reading the free pocket guide for the past several days, and I noticed that it seems to suggest the two partition, one for each OS, method. Although it appears that the partitioning options have changed since 8.10, as "Guided--Resize Partition" no longer seems to be an option.

Is this how things are generally done now? If so, why the shift away from having a separate data partition or a separate home partition? Don't we lose the convenience of being able to quickly and easily perform a clean install of a new OS? If it is still advisable to include a separate data partition, how should one go about setting this up, and what file system should the partition be? Should it be "shared" between Windows and Ubuntu?

In any case, I hope my confusion and my question is clear at this point. This is my home computer, so I use it primary for internet, watching video, playing games, programming, and some occasional work that would require Windows. For the most part, I'd rather use Ubuntu unless I absolutely need to use Windows to run a particular software.

Thanks very much!

---

### Post by sandyd on 2010-06-04
> **canac said:**
> I should mention first that I'm new to this, but I have spent some time researching the issue. However, I can't quite seem to find the information I'm looking for.

I would like to dual boot Windows 7 x32 and Ubuntu 10.04. I've managed to successfully do this, but I would like to make sure I do it in a way that's "good" and generally makes sense. The trouble I'm having is that a lot of the information out there seems to be outdated, particularly with respect to hard drive partitioning. For instance, [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) seems to indicate, with the statement, "[this tutorial's] general guidelines and principles are still valid, but at this point in computing history, I think the idea of a traditional dual-boot with separate partitions for each OS and then a possible shared partition is a bit antiquated," that partitioning or the traditional idea of partitioning is now obsolete.

**Linux now has support for NTFS, so you can actually read the windows partition from linux ;) therefore, no intermediary partition is needed.**

If this is the case, then what's taken its (separate partitions for each OS and data) place? As a relatively new (to Ubuntu) user and starting with a clean drive, how should I go about partitioning or not partitioning my drive during installation?

For what it's worth, just for experimentation, I installed the dual boot two ways. First, by installing Windows and then shrinking the partition in Windows, and then installing Ubuntu on the unallocated space. Then, thinking it would be smart to have a separate data partition, I formatted, used GParted running off the CD to create my 3 partitions, then installed Windows, followed by Ubuntu.

I've been reading the free pocket guide for the past several days, and I noticed that it seems to suggest the two partition, one for each OS, method. Although it appears that the partitioning options have changed since 8.10, as "Guided--Resize Partition" no longer seems to be an option.
[B]
This was done for an important reason. if you try resizing the windows 7 partition through the ubuntu installer, or anything other than the native windows partitioning tool, windows will go kaput and you will have to do a disk check from the recovery cds.
[/B] 
Is this how things are generally done now? If so, why the shift away from having a separate data partition or a separate home partition? Don't we lose the convenience of being able to quickly and easily perform a clean install of a new OS? If it is still advisable to include a separate data partition, how should one go about setting this up, and what file system should the partition be? Should it be "shared" between Windows and Ubuntu?
**See above**

In any case, I hope my confusion and my question is clear at this point. This is my home computer, so I use it primary for internet, watching video, playing games, programming, and some occasional work that would require Windows. For the most part, I'd rather use Ubuntu unless I absolutely need to use Windows to run a particular software.

Thanks very much!.

---

### Post by sydbat on 2010-06-04
Basic dual boot partitioning scheme...

1) Install Windows first.
 
1a) The Windows installer used to allow you to make partitions, and if this is still the case, create an NTFS for Windows, an NTFS for the share and 3 other partitions with no formatting.

1b) Depending on the size of your drive, the first NTFS should be no less than 20GB (to allow updating of Windows) and the second however big you want the share to be (some people might suggest no need for a separate share, but I have found that when you have to reinstall Windows, it keeps your data intact...kinda like a separate /home).

1c) The first, second and third non-formatted partitions can be however big you want them...I suggest 10GB for the first (for /), 20GB + for the second (for /home) and the third about the same as your RAM (for /swap...if you feel you need this at all).

2) Install your Linux distribution of choice into the first unformatted partition and tell the installer to set up the next 2 as I suggested.

3) You are good to go.

This is the way I would do it, so I hope it helps a bit.

---

### Post by sites on 2010-06-04
I disagree.  Creating the partitions for Ubuntu while in Windows isn't necessary and when you install Windows don't create any partition other than the one for the OS because the linux swap partition should be as close to the beginning of the hard drive as you can get it.  After Windows is installed, reboot and start installing Ubuntu. Choose manual partitioning during the install.  The FIRST linux partition should be for swap, twice the size of your total RAM for best performance.  The second partition should be for / and should be 10-12GB.  The next spot is for /home but leave enough space for the shared partition.  After Ubuntu is installed, reboot into Windows and use the remaining space as your shared partition.

This is the way i've been doing it for years, but if anyone has objections i'd be glad to know what they are.

---

### Post by sydbat on 2010-06-04
> **sites said:**
> I disagree.  Creating the partitions for linux while in Windows isn't necessary.  Choose manual partitioning during the Ubuntu install.  The FIRST linux partition should be for swap, twice the size of your total RAM for best performance.  Swap should be as close to the beginning of the drive as possible so hold off making your shared partition until after installing Ubuntu.  The second partition should be for / and should be 10-12GB.  The next spot is for /home but leave enough space for the shared partition.  Reboot into windows and use the remaining space as your shared partition.You are correct - the first Linux partition should be /swap, although depending on the amount of RAM you have, it does not have to be twice the size.

Also, you can create all the partitions with whatever you choose, I just did it from the Windows installer while in it.

---

### Post by sites on 2010-06-04
> **sydbat said:**
> You are correct - the first Linux partition should be /swap, although depending on the amount of RAM you have, it does not have to be twice the size.

Also, you can create all the partitions with whatever you choose, I just did it from the Windows installer while in it.

Yeah, my rule of thumb for swap is never any more than 8GB.  I've had 4GB RAM in most of my machines for a few years now, but depending on how you're using the machine YMMV.  I run a lot of VM's so the more the merrier.  And i just prefer to let linux make it's own partitions, because i like snubbing Winderz :)

Cheers

---

### Post by canac on 2010-06-04
Thank you for the replies. I have a few more questions, if you don't mind.

If the goal is to get /swap as close to the front of the drive as possible, should I install Ubuntu in front of Windows (assuming it makes sense to ask this question)? Given 4 GB of RAM and a 250 GB hard drive, the drive would look something like:

/swap (8 GB) | / (12 GB) | /home (20 GB) | shared (160 GB) | Windows (50 GB)

Or maybe switch shared and Windows?

Also, I could have missed it, but both times I installed Windows recently, I didn't see an ability to repartition the drive during installation, and I did look for it. Perhaps I could have missed it. Does anyone know for sure?

This was why, when I tried a second installation, I first used GParted off live CD to set up the partitions. If I recall correctly, the Windows installer lets me select which partition I want to install it to, as does Ubuntu, so I could install them in any arbitrary order. It seems no one else has done it this way though. Is there a reason for that?

---

### Post by srs5694 on 2010-06-04
> **canac said:**
> The trouble I'm having is that a lot of the information out there seems to be outdated, particularly with respect to hard drive partitioning. For instance, [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) seems to indicate, with the statement, "[this tutorial's] general guidelines and principles are still valid, but at this point in computing history, I think the idea of a traditional dual-boot with separate partitions for each OS and then a possible shared partition is a bit antiquated," that partitioning or the traditional idea of partitioning is now obsolete.

If this is the case, then what's taken its (separate partitions for each OS and data) place? As a relatively new (to Ubuntu) user and starting with a clean drive, how should I go about partitioning or not partitioning my drive during installation?

I believe you're misinterpreting the comments on the psychocats.net site. The claim isn't that partitions are obsolete, but that traditional dual-boot installations are obsolete. What replaces these installations, according to the author, is virtualization -- running one OS inside another one.

There's certainly merit to this viewpoint, but there are situations where dual-boot configurations make sense, and judging by posts here, they're still very popular, at least among Ubuntu users.

> I've been reading the free pocket guide for the past several days, and I noticed that it seems to suggest the two partition, one for each OS, method. Although it appears that the partitioning options have changed since 8.10, as "Guided--Resize Partition" no longer seems to be an option.

Is this how things are generally done now? If so, why the shift away from having a separate data partition or a separate home partition? Don't we lose the convenience of being able to quickly and easily perform a clean install of a new OS? If it is still advisable to include a separate data partition, how should one go about setting this up, and what file system should the partition be? Should it be "shared" between Windows and Ubuntu?

You're quite right; the advice to use just two filesystem partitions (one each for Windows and Linux) is limiting. IMHO, it's bad advice. My own basic dual-boot recommendation would look something like this:

/dev/sda1 - Windows C: (NTFS)
/dev/sda2 - Extended (holds all of the following)
/dev/sda5 - Shared data (FAT, NTFS, or ext2/3)
/dev/sda6 - Linux root (/)
/dev/sda7 - Linux swap
/dev/sda8 - Linux /home

There are many possible variants on this, of course, and many of them have their merits.

FWIW, I would *not* recommend giving Linux direct access to the Windows C: partition except for temporary/emergency maintenance, nor would I recommend giving Windows direct access to the Linux root (/) partition, and probably not to /home. The reason is that neither OS fully understands or honors the others' security features. This makes it too easy to create files that won't be readable by ordinary users of the other OS or to damage files that shouldn't be altered. Although you can often get away with direct access, it's like Russian Roulette -- sooner or later you'll get yourself in trouble. A shared data partition minimizes the risks of problems, since no critical system or account files reside in that partition.

---

### Post by srs5694 on 2010-06-04
> **canac said:**
> Thank you for the replies. I have a few more questions, if you don't mind.

If the goal is to get /swap as close to the front of the drive as possible, should I install Ubuntu in front of Windows (assuming it makes sense to ask this question)? Given 4 GB of RAM and a 250 GB hard drive, the drive would look something like:

/swap (8 GB) | / (12 GB) | /home (20 GB) | shared (160 GB) | Windows (50 GB)

Or maybe switch shared and Windows?

I'm not the one who recommended putting swap at the start of the disk, and I don't know of any reason for doing so. (Note, BTW, that swap space is not mounted, so referring to it with a leading slash, as in "/swap", is pointless at best and misleading at worst.) In theory, the start of most disks is the slowest part, so putting swap space there makes little sense. Putting it at the end might make more sense by this logic. I've just run a few tests, though, and I see no reliable and big performance difference on the disks I've tested.

Another factor is disk head seeks. To minimize time lost to them, you'd want to put the swap space in the middle of the disk, or at least in the middle of the Linux partitions. (That's why I  put it between the two Linux filesystem partitions in my suggested layout in my previous message.) These are both theoretical arguments, though; in practice, you'd need to run tests on *your* disks with *your* usage patterns to know what works best. You'll spend far more time doing such tests than you'd be likely to gain by optimizing your swap performance. Also, since most systems today have enough RAM to render swap space fairly unimportant, the question of where best to put it is equally unimportant.

> This was why, when I tried a second installation, I first used GParted off live CD to set up the partitions. If I recall correctly, the Windows installer lets me select which partition I want to install it to, as does Ubuntu, so I could install them in any arbitrary order. It seems no one else has done it this way though. Is there a reason for that?

I don't know why the guides you've read don't do it this way. Personally, I prefer using Linux partitioning tools to set up all my partitions, including those for Windows, before I begin. This is because I'm familiar with the Linux tools and I know they'll do what I want them to do. Somebody who's more familiar with other tools might prefer to use them, or might prefer to use a mixed set of tools.

---

### Post by canac on 2010-06-04
> **srs5694 said:**
> 
FWIW, I would *not* recommend giving Linux direct access to the Windows C: partition except for temporary/emergency maintenance, nor would I recommend giving Windows direct access to the Linux root (/) partition, and probably not to /home. The reason is that neither OS fully understands or honors the others' security features. This makes it too easy to create files that won't be readable by ordinary users of the other OS or to damage files that shouldn't be altered. Although you can often get away with direct access, it's like Russian Roulette -- sooner or later you'll get yourself in trouble. A shared data partition minimizes the risks of problems, since no critical system or account files reside in that partition.

This makes sense, but I'm not sure how I would go about denying Ubuntu access to the Windows partition. Windows seems unable to access Ubuntu. I assume this is due to its inability to recognize the ext4 file system, but I can't rely on this when it's the other way around since Ubuntu now supports NTFS. What's the solution?

---

### Post by oldfred on 2010-06-05
I agree with srs5694.

Also if you have more than 3GB of RAM you will not be using swap much if at all unless you are editing videos, load every program at once or other very large applications. Some now recommend no swap but I think you still need it. Swap can be 2GB, or if you want to hibernate make it slightly larger than RAM since it is used for hiberantion. Swap used to be twice RAM when RAM was 256MB or 512MB, now with GB of RAM swap is not used nearly as much.

Even windows users often recommend a separate data partition so when windows has to be reinstalled you do not lose your data. I use a separate shared NTFS partition and only read the windows system install. I use the shared for firefox and thunderbird profiles so I have the same bookmarks and emails in both systems. If installing other operating system a separate ext3 or ext4  /data partition makes sense as you can easily use that in all linux systems

---

### Post by srs5694 on 2010-06-05
> **canac said:**
> This makes sense, but I'm not sure how I would go about denying Ubuntu access to the Windows partition. Windows seems unable to access Ubuntu. I assume this is due to its inability to recognize the ext4 file system, but I can't rely on this when it's the other way around since Ubuntu now supports NTFS. What's the solution?

Ordinarily, Linux only mounts partitions listed in /etc/fstab, so omitting the Windows C: partition from there will do the job; however, user-oriented distributions such as Ubuntu often provide other means of mounting partitions. Personally, I usually disable such methods right off the bat, since I dislike them. I'm therefore unsure how easy it is to accidentally mount a Windows C: partition in Linux. If this becomes a problem, something like the following entry in /etc/fstab might help:

```

/dev/sda1        /media/winc    ntfs        noauto,owner    0 0

```

Ensure that /media/winc exists and give ownership of that directory to root. In theory, this should keep it from being automatically mounted, and you won't be able to mount it as an ordinary user. The root user will still be able to mount it (in other words, you'll be able to do so with the help of sudo, as in "sudo mount /media/winc"), but it won't mount automatically.

---

