---
title: "Quick partitioning question..."
date: 2010-04-06
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2010-04-06
Background:

Currently I have my laptop hard drive all messed up with it's partitions, with Vista / ubuntu / recovery / media direct from dell.  When Lucid is finally released, I am going to do a clean install.  I also have a Windows 7 license and as much as I dislike Windows, I need it for work because I am in IT and need to be familiar with the system. 

Problem:

Should I first install Windows 7 on the whole hard drive, and then install Ubuntu over it and shrink Windows to 50gb or so?

Should I first install Ubuntu and then install Windows 7?

Should I use gparted to partition my hard drive before hand and then install to each given section?

Any ideas/feedback/help/experience is welcome.

---

### Post by MooPi on 2010-04-06
Sounds like a wonderful time to experiment. But I think the two choices that should work the best would be partition first then install, and the second would be install 7 first resize the partition and install Ubuntu. I've used both methods and prefer using gparted then install. Make certain you format to a file system incompatible to Microsoft for your space reserved for Ubuntu.

---

### Post by Paqman on 2010-04-06
> **x C0MMAND0 x said:**
> 
Should I use gparted to partition my hard drive before hand and then install to each given section?


Doing it this way could save a lot of time. Shrinking partitions can be really slow. At the very least, create an NTFS partition leaving the space for Ubuntu empty, install Windows, then install Ubuntu into the empty space.

---

### Post by jimbren on 2010-04-06
I'd do it exactly as Paqman suggested.  Easier and faster than shrinking the partition later.  


If you do decide to install Windows then shrink the partition, make sure you defrag from within Windows first, even if you're doing one install right after the other.

---

### Post by Nisal on 2010-04-06
what about installing inside windows :P

---

### Post by undecim on 2010-04-06
Partition ahead of time to save a lot of time.

A few things I would make sure of:

Install Windows first.

Make a /home/ partition for Ubuntu. The / partition can be 5-10 GB depending on how much stuff you install

Decide if you really need a swap partition. If you have 2GB or more ram, you probably won't ever use it unless you want to use the hibernation feature, in which case make sure you have more swap space than ram.

Make the Windows partition larger than the Ubuntu partition. Windows can't touch Ubuntu partitions, but Ubuntu can use Windows partitions. You can always symlink ~/Music/ and other folders to your folders on your Windows partition.

---

### Post by jimbren on 2010-04-06
> **Nisal said:**
> what about installing inside windows :P

Personally, I'd do an install of Ubuntu and do a VM for Windows, but I suppose it depends on what you use more.  

One of the advantages to doing it this way is that it's easier to recover if you have some kind of loss.  I always make a separate partition for /home and do backups of it, including my Virtual Box VM.  Then if I need to restore or decide to upgrade to the new release, I can leave /home alone and do a clean install.

---

### Post by srs5694 on 2010-04-06
> **undecim said:**
> Make the Windows partition larger than the Ubuntu partition. Windows can't touch Ubuntu partitions, but Ubuntu can use Windows partitions. You can always symlink ~/Music/ and other folders to your folders on your Windows partition.

I disagree with this. As a general rule, I try to avoid giving any OS direct access to any other OS's installation/root filesystem, since doing so is inviting problems. Although NTFS-3g (which Ubuntu uses for its NTFS support) seems pretty solid, it's a third-party driver, and of course Linux has no innate understanding of Windows-specific files.

Instead, I recommend creating a Windows boot partition that's big enough for Windows and its programs, the Linux partitions already discussed here (root, /home, and swap), and another partition to hold shared data files. This last partition can be FAT if you don't expect to store files bigger than 4GB on it, but these days that's not a very safe assumption, so you may need to use NTFS or perhaps ext2fs or ext3fs along with Windows drivers for them. (I'm not sure how reliable the Windows ext2fs/ext3fs drivers are, though.) If you do it this way and keep the Windows boot partition from mounting in Linux, you greatly reduce the risk of accidentally damaging it from Linux.

---

### Post by LewRockwellFAN on 2010-04-07
I'd partition first. Either the W7 partitioner or Gparted - they both work fine. But you'll save a lot of work if you INSTALL W7 first, and to the first partition. Otherwise you'll have to grub about with GRUB. I'd give it 35 GB if you have plenty of room, but 20 should be ok. Ubuntu I'd give 15 GB although half that would be ok. Assuming you want to share data between the OSs I would use the rest of the space for a big fat FAT 32, if you'd like to be able to set and unset the read only attribs of files or an NTFS if you don't care about that (Ubuntu doesn't handle NTFS permissions properly yet). If you want the permissions propriety of FAT 32 but occasionally need to deal with a DVD iso or other file over 4 GB make one of each with the size according to how many such files you want to store. You can always split isos to store them on the FAT and join them prior to use in the NTFS if you need to.

---

### Post by x C0MMAND0 x on 2010-04-07
> **undecim said:**
> Partition ahead of time to save a lot of time.

A few things I would make sure of:

Install Windows first.

Make a /home/ partition for Ubuntu. The / partition can be 5-10 GB depending on how much stuff you install

Decide if you really need a swap partition. If you have 2GB or more ram, you probably won't ever use it unless you want to use the hibernation feature, in which case make sure you have more swap space than ram.

Make the Windows partition larger than the Ubuntu partition. Windows can't touch Ubuntu partitions, but Ubuntu can use Windows partitions. You can always symlink ~/Music/ and other folders to your folders on your Windows partition.

Why would I want a partition just for /home/, and I don't really know/understand what a swap partition is.  I have 4gb of ram and never hibernate.  

If I have a separate /home/ partition, then I would have 3 partitions

1. Windows 7 (30gb)
2. /home (?gb)
3. Ubuntu OS (?gb)

How do I know how big to make the /home/ partition?  I am always adding new music / movies to my collection, so I need my /home/ to be really big.  What is the advantage of having a separate /home/ partition?

---

### Post by derande on 2010-04-07
> **x C0MMAND0 x said:**
> Why would I want a partition just for /home/, and I don't really know/understand what a swap partition is.  I have 4gb of ram and never hibernate.  

If I have a separate /home/ partition, then I would have 3 partitions

1. Windows 7 (30gb)
2. /home (?gb)
3. Ubuntu OS (?gb)

How do I know how big to make the /home/ partition?  I am always adding new music / movies to my collection, so I need my /home/ to be really big.  What is the advantage of having a separate /home/ partition?

1. Windows 7 (30gb)
2. Ubuntu (10-15gb)
3. Storage (rest of your hard drive space if you don't plan on making a swap partition)

separating your /home partition from your /storage partition allows you to update or change your /home directory OS without affecting any of your personal data files in /storage.

very helpful if you need to reinstall the OS w/out losing your goodies.

made /home 10-15gb (which is probably generous). you don't need that much for the programs.

---

### Post by x C0MMAND0 x on 2010-04-07
Ahh, I'm starting to understand...So /home is where Ubuntu is installed?  But what about /etc and all of the other folders?  Will those all be installed to /home?  Then for the /storage partition that is where I would have my music/pictures/videos/files?

I guess I'm still a little confused as to where I would go to access all of my files if I did have it set up this way.  Currently, I go to /home/user/all_my_files, but if Ubuntu is installed to /home then where would I go to access all of my files?

Thanks for the help I think after a little more discussion I will understand.

---

### Post by da burger on 2010-04-07
/home is not where ubuntu lives. The /home partition only holds your /home folder. You also need a root partition which contains /etc /boot /var and many others. I do not understand swap but I know that the ubuntu installer should make a swap partition for you. The advantage to a separate /home is that you can reinstall ubuntu without losing your files.

---

### Post by srs5694 on 2010-04-07
> **x C0MMAND0 x said:**
> Why would I want a partition just for /home/,

Your user files go there. Keeping /home separate means that you can easily upgrade the OS without messing with your user data. (Some upgrade methods permit relatively safe upgrades even without a separate /home partition, but keeping /home separate increases your options, up to and including switching to an entirely different distribution.)

> and I don't really know/understand what a swap partition is.  I have 4gb of ram and never hibernate.

Swap space is used as a supplement to RAM; when the system runs out of RAM, the system uses swap space. It's also used when you hibernate (suspend to RAM). Windows and OS X also use swap space, but they generally use a file on the normal filesystem for this purpose, whereas Linux traditionally uses a separate partition. Personally, I recommend creating a swap partition even if you've got plenty of RAM and don't hibernate, since the swap space serves as a buffer in case you ever do something that requires an unusual amount of memory. Modern hard disks can easily spare a few gigabytes for this purpose.

> If I have a separate /home/ partition, then I would have 3 partitions

1. Windows 7 (30gb)
2. /home (?gb)
3. Ubuntu OS (?gb)

The "Ubuntu OS" is also known as the "root" or "/" partition. You'll have four partitions if you add a swap partition, and more than that if you install Windows in certain ways. (Some Windows installation methods use two or more partitions.) You may also want a partition for shared files -- anything you'd want to access from either OS.

> How do I know how big to make the /home/ partition?  I am always adding new music / movies to my collection, so I need my /home/ to be really big.

I recommend you set the size of /home and the shared-data partition based on what's left over after you allocate OS space (30GB for Windows, as above, seems reasonable. I'd give 5-20GB to Linux, depending on how big an installation you want.) Only you can know how much user data you expect to share vs. use in only one OS. If you want to access those music and movie files in both OSes, then make your shared-data partition big enough for them, and /home proportionally smaller. If you only want to access your media files in Linux, then /home can be bigger and the shared-data partition smaller.

> **derande]
1. Windows 7 (30gb)
2. /home (10-15gb) >>> this is your Ubuntu OS
3. /storage (rest of your hard drive space if you don't plan on making a swap partition)
[/quote]

#2 is definitely incorrect and #3 is odd. ***The Ubuntu OS is not installed in the /home directory!!*** I don't mean to scream said:**
> Filesystem Hierarchy Standard,[/url] should you be interested in looking it up.

[quote=derande]separating your /home partition from your /storage partition allows you to update or change your /home directory OS without affecting any of your personal data files in /storage.

If you substitute "root (/)" for "/home" and "/home" for "/storage", this is correct. As stated, though, it's very misleading.

---

### Post by undecim on 2010-04-07
> **x C0MMAND0 x said:**
> Ahh, I'm starting to understand...So /home is where Ubuntu is installed?  But what about /etc and all of the other folders?  Will those all be installed to /home?  Then for the /storage partition that is where I would have my music/pictures/videos/files?

I guess I'm still a little confused as to where I would go to access all of my files if I did have it set up this way.  Currently, I go to /home/user/all_my_files, but if Ubuntu is installed to /home then where would I go to access all of my files?

Thanks for the help I think after a little more discussion I will understand.

I think there is some misunderstandings going on here...

Let me give you an example. If I installed Ubuntu to a 100 GB blank hard drive and had 2048 MB of ram and wanted a seperate home partition, I would probably have something like this:

/dev/sda1 as / - 10 GB.

/dev/sda2 as /home/ - Just under 88 GB

/dev/sda5 as swap - Just over 2 GB.


Ubuntu installs to /. All my programs will go in /usr, system-wide settings, in /etc/ and so on. All of this is on sda1 because /usr, /etc, /var... are all children of the / directory.

However, my music, documents, and my user settings (firefox bookmarks, empathy accounts... anything I don't need administrative access to set up) would be in /home/undecim. Since I have a separate home partition, it will be stored in the /undecim folder on /dev/sda2.

The swap partition acts as sort of extra RAM. Obviously, it's slower than normal ram, which is why Ubuntu usually uses normal RAM first. But if you run out of memory, the kernel stores the least-access memory data there until some space is freed up in the ram. Additionally, when you use hibernation, all your memory is dumped to the swap partition so that it can be brought back after the computer has been turned off. If you have plenty of ram and don't care about hibernation, then there is no need to spend 2GB on swap, and instead would have a 90GB home partition.

Now, suppose I decide I don't like Ubuntu and want to try OpenSuse. In that case, I can just stick in an OpenSuse install CD and install to /dev/sda1, set /dev/sda2 as home (without formatting it!) and I will have OpenSuse installed, but all my music, documents and application settings will still be on the /home partition which wasn't touched. This is why most experienced Linux users recommend a separate home directory - It gives you the ultimate freedom to install new distros. 


Now, lets add Windows to the picture.

As I said before, Windows cannot access Ubuntu partitions, but Ubuntu can access Windows partitions. My suggestion was to use the Windows partition to store all your Music and other large directories using symlinks. Let's say you choose to mount Windows 7's partition on /win7, and set up the permissions for you to use it. You can then run "ln -s /win7/Users/username/Music ~/Music" and then your Music directory will point to the Music directory on windows. That way, you have your music on both Windows and Ubuntu without using your hard drive space twice.

You could also use srs5694's suggestion of another partion in a format that Windows can read. Then store there anything you want to share between Windows and Ubuntu. This is probably a better idea, since if Windows breaks its own filesystem, you are less likely to lose your data.

---

### Post by derande on 2010-04-07
> **srs5694 said:**
> Your user files go there. Keeping /home separate means that you can easily upgrade the OS without messing with your user data. (Some upgrade methods permit relatively safe upgrades even without a separate /home partition, but keeping /home separate increases your options, up to and including switching to an entirely different distribution.)



Swap space is used as a supplement to RAM; when the system runs out of RAM, the system uses swap space. It's also used when you hibernate (suspend to RAM). Windows and OS X also use swap space, but they generally use a file on the normal filesystem for this purpose, whereas Linux traditionally uses a separate partition. Personally, I recommend creating a swap partition even if you've got plenty of RAM and don't hibernate, since the swap space serves as a buffer in case you ever do something that requires an unusual amount of memory. Modern hard disks can easily spare a few gigabytes for this purpose.



The "Ubuntu OS" is also known as the "root" or "/" partition. You'll have four partitions if you add a swap partition, and more than that if you install Windows in certain ways. (Some Windows installation methods use two or more partitions.) You may also want a partition for shared files -- anything you'd want to access from either OS.



I recommend you set the size of /home and the shared-data partition based on what's left over after you allocate OS space (30GB for Windows, as above, seems reasonable. I'd give 5-20GB to Linux, depending on how big an installation you want.) Only you can know how much user data you expect to share vs. use in only one OS. If you want to access those music and movie files in both OSes, then make your shared-data partition big enough for them, and /home proportionally smaller. If you only want to access your media files in Linux, then /home can be bigger and the shared-data partition smaller.



#2 is definitely incorrect and #3 is odd. ***The Ubuntu OS is not installed in the /home directory!!*** I don't mean to scream; I just want to make this crystal clear. /home is where *user data* goes. The system is installed in the root filesystem (/), and mostly in the /usr subdirectory, *not* /home.

Although there's no rule against creating a directory called /storage and putting user files there, the default location for user files in Linux is /home, and subdirectories thereof that are normally named after your account name. For instance, if your username is paqman, you'd have /home/paqman; if somebody else who uses the computer has an account called mspaqman, that user's home directory would be /home/mspaqman.

If you create a cross-OS storage partition, you could mount it at /storage, at /home/paqman/shared, or at almost any other location. (You wouldn't use normal system directories, such as /usr or /bin.) The layout of Linux directories is described in the [Filesystem Hierarchy Standard,](http://www.pathname.com/fhs/) should you be interested in looking it up.



If you substitute "root (/)" for "/home" and "/home" for "/storage", this is correct. As stated, though, it's very misleading.

please excuse that - copy/paste error

---

### Post by Steven_S on 2010-04-07
Good thing I read on :-). 

I would like to chime in with a small request for clarification (as it regards the topic directly). Let's say that I play a game in Ubuntu, and save my progress. Would the game itself then be in the root partition (/) and the game-saves in my own /home? And does that mean that, if I do a fresh install of for example a new version of Ubuntu, the game-saves would still be accessible by a fresh install of the game itself?

---

### Post by undecim on 2010-04-07
> **Steven_S said:**
> Good thing I read on :-). 

I would like to chime in with a small request for clarification (as it regards the topic directly). Let's say that I play a game in Ubuntu, and save my progress. Would the game itself then be in the root partition (/) and the game-saves in my own /home? And does that mean that, if I do a fresh install of for example a new version of Ubuntu, the game-saves would still be accessible by a fresh install of the game itself?

It depends on the game. Most games will save to a dotfile in your home directory, especially save-games. High scores can sometimes be a different issue though

If you want to test a game for that, you can create a new user and see if you and the new user share high scores. If they don't then the scores are stored in your home directory.

I don't know of any games in the repos that store scores out side of the home directory though.

---

### Post by Steven_S on 2010-04-07
Thanks for that answer! I use the example of games because I am trying to figure out how many user settings would be saved with a fresh install. Documents go on a different disk alltogether, so that doesn't matter. But the prospect of having to re-do settings on all the installed software might be a bit too much for me (and may prompt me to stay with Karmic as long as it is supported). 

Guess I'll just have to test :-).

---

### Post by tom.swartz07 on 2010-04-07
> **Steven_S said:**
> Thanks for that answer! I use the example of games because I am trying to figure out how many user settings would be saved with a fresh install. Documents go on a different disk alltogether, so that doesn't matter. But the prospect of having to re-do settings on all the installed software might be a bit too much for me (and may prompt me to stay with Karmic as long as it is supported). 

Guess I'll just have to test :-).

I have my /home folder on a separate partition and, just like they have mentioned before, most (if not all) of your customizations are saved over.

For example, I have a specific configuration of Docky and Avant Window Navigator, as well as Compiz and Conky. All of them are preserved between different installs. The general consensus is that the majority of your settings will be saved. 

Granted, you shouldnt assume that because it's on a different partition you shouldnt back it up.... 
Before you do anything drastic, even upgrade in a few weeks, you should back up your stuff just in case! :popcorn:

---

### Post by Steven_S on 2010-04-08
Will do! I would have to move /home to its own partition first though (haven't done that on install). 

I must say I am mucking about with Ubuntu just now and then, when I have the time. The biggest challenge seems to be to get the ntfs disks in my system mounted correctly and with the right file permissions. There is a lot of information (too much for a newbie) around on what to do, but I need to synthesise and write down what would work for me and for what I want. 

On the one hand, it is bothersome that this doesn't just work, but it is also interesting because I am figuring out how this grey box in the corner actually works and why it does what it does. I have a feeling that might be useful in the future :-). 

Still, if there is one thing that would tempt people with additional ntfs disks and a network environment with Windows systems to try and then dump Linux, I have a feeling it is this precise issue. But I'm getting off-topic here...

---

### Post by LewRockwellFAN on 2010-04-11
> **Steven_S said:**
> 
Still, if there is one thing that would tempt people with additional ntfs disks and a network environment with Windows systems to try and then dump Linux, I have a feeling it is this precise issue. But I'm getting off-topic here...

Dittos on that. For me, part of the solution (most would disagree) seems to be the traditional approach: use FAT 32 for most of your data. There are disadvantages. FAT doesn't deal with power outages well. But with a UPS who cares? It won't take > 4 GB files. Of which most will have few if any. A very few isos of DVDs is about it. Saboyan I think is that big, maybe. If you do need an NTFS it will help to mount it ntfs-3g instead of ntfs in fstab. Not sure why it doesn't default that way. Maybe just something nobody has gotten around to changing or maybe the idea was to make it a little harder to go root around in a Windows system partition and bork it. There is a thread around here somewhere in which some real knowledgable people guided me in revising fstab to make my data partitions work better. I can't seem to find it now. Maybe it was on another forum. But 90% of the solution to making data partitions accessible to several OSs practical lies in fstab. Not sure about the other 10%. Still working on it myself.

---

