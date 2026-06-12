---
title: "I have a dilema with partitions."
date: 2010-12-31
forum: New to Ubuntu
---

### Post by jink2002 on 2010-12-31
Hi there. I'm new to using Ubuntu, and, quite frankly, I'm a bit of a fish out of water, being a Windows user for so long. However, I've been doing pretty well getting the hang of applications and troubleshooting until this happened. I originally had a Windows XP partition on this laptop. Then I used an application to install Ubuntu from Windows onto a new partition, therefore making two total. After a while, the XP partition became corrupted and I was no longer able to access it. Now, everything I do is on Linux (and I'm liking it a lot lol). The only problem is I've now run out of space (I'm now down to about half a gig). My harddrive is (I believe) 250 GB, but I only made this partition a little over 30 GB. My question is how do I change my partition size, or better yet, delete the Windows partition all together and have Ubuntu take advantage of all 250 GB?

Sorry if this has been asked before, and for giving so much background information. However, I'm very new to Linux and I wanted to make sure that I wasn't leaving anything important out. 

Thank you.

---

### Post by Rubi1200 on 2010-12-31
Hi and welcome to the forums :-)

From the terminal in Ubuntu:
```
sudo parted -l
```

(lowercase L not 1)

Post the output here please

Thanks

---

### Post by sprintexec on 2010-12-31
Hi,

Which version of ubuntu are you using? This may make a difference to the suggested way forward. The version I'm using has a disk utility under the preferences tab which I believe can be used to alter the size of the partitions. However before you get into any of this I'd read around, take soundings and back up your data. Good luck, AJ

---

### Post by jink2002 on 2010-12-31
Wow, fast reply, haha. Not used to this on other forums. I HAVE FOUND MY FAMILY

*Ahem*....sorry. Anyway, Rubi1200, this is the output:

Model: ATA WDC WD3200BEKT-6 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot


Guess it's a 320 gig afterall. 


And sprintexec, I believe I am using the most current version of Ubuntu 10.10

I guess should also point out that this is a laptop I built myself, not bought from a store. Not sure if that makes a difference...

---

### Post by Paqman on 2010-12-31
It looks like you've installed using Wubi, which is a bit of a special case. Instead of installing Ubuntu to its own partition, Wubi installs it to a virtual partition that's actually just a big file on the Windows partition. This means you can't just delete the Windows partition and expand Ubuntu.

You've got a couple of options:
[list]
[*] Create a new partition for Ubuntu and try using [LVPM]("http://lubi.sourceforge.net/lvpm.html") to migrate your Wubi install to it.
[*] Reinstall Ubuntu, using the entire disk.
[/list]

Apparently there are problems with LVPM and recent versions of Ubuntu, so a reinstall might be the way forward. You can always take a backup of your home folder and paste it back in if you want to retain all your data and settings.

---

### Post by jink2002 on 2010-12-31
Yeah I used Wubi. Ok, looks like I'll reinstall everything then. Is there a tutorial for that that someone can point me to (preferably in Layman's terms lol)

---

### Post by ajgreeny on 2010-12-31
Here you go!
[Separate /home at installation]("http://www.psychocats.net/ubuntu/installseparatehome") 
This site tells you everything and gives you a separate /home partition, well worth having on a big disk like yours.

---

### Post by Rubi1200 on 2010-12-31
The best guide for migrating a Wubi install to disk can be found at the end of the first post here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Kellemora on 2010-12-31
Hi Jink

I'm going to bump against AJ's advice here!

Although having /home on it's own partition makes updates, upgrades and many other things much easier.  EG moving to another computer or backing up your settings.

It has a major downfall, which I discovered the hard way.

You can't have a /home partition when trying out many different Distro's or moving from Ubuntu 64 bit to a new machine with 32 bit Ubuntu.

If you have 8.04 32 bit, 8.04 64 bit, 10.04.1 64 bit & 10.04.1 32 bit all on the same machine, sharing the same /home partition.
Any cleanup feature used wipes out the files required for the other versions if not used in the current version you are booted into.
Also, it self-corrupts!  Replacing a version of something EG FLASH 32 used on 8.04 32 bit with Flash 64 used on 10.04.1 64 bit.

By allowing the OS to install /home on it's own partition has eliminated 100% of the problems I encountered by having /home on it's own partition.

BUT, I should note that I DO NOT use /home for Data Storage as 99% of the folks do.  Because I have many computers, I use the equivalent of a File Server to store all Data that I want to maintain and have available.  A computers internal drive with an external Hard Drive plugged into it, utilizing only ONE of the computers we simply call our file server computer, nothing more than File Sharing actually.  The internal is mirrored to the external. Then 3 times a day the external is backed up off-site.  We also maintain a known good backup (mirror not actual backup) that is not automatically overwritten).  A corrupt file, backed up over a good file, will corrupt the good file by replacing it with the corrupt file.  RSync can be set to only copy changed files and let you check them before archiving them onto the primary data backup drive.

You can still keep your Windows on that large of a hard drive.
I only give Ubuntu about 50 gigs of space and it's never run out.
But if you store data, I would give Windows 100 gigs, Ubuntu, 100 gigs and use the remainder for trying out different things and/or extra storage space for music, videos, images, important data files, etc.

TTUL
Gary

---

### Post by Paqman on 2010-12-31
> **Kellemora said:**
> 
You can't have a /home partition when trying out many different Distro's or moving from Ubuntu 64 bit to a new machine with 32 bit Ubuntu.

If you have 8.04 32 bit, 8.04 64 bit, 10.04.1 64 bit & 10.04.1 32 bit all on the same machine, sharing the same /home partition.
Any cleanup feature used wipes out the files required for the other versions if not used in the current version you are booted into.
Also, it self-corrupts!  Replacing a version of something EG FLASH 32 used on 8.04 32 bit with Flash 64 used on 10.04.1 64 bit.


The simple solution to that is to use a different account name on each distro. I've had one shared home partition for many distros for years. If you use a different login on each system then the files are kept nice and separate in the different directories. Eg:

/home/username_on_distro1
/home/username_on_distro2
/home/username_on_distro3

No mess, no fuss.

---

### Post by ajgreeny on 2010-12-31
> You can't have a /home partition when trying out many different Distro's  or moving from Ubuntu 64 bit to a new machine with 32 bit Ubuntu.
I have overcome this multi distro problem of a separate /home partition by keeping all the hidden config folders and files of  the new distro's home in the default home folder of its root partition and then simply making links to the data folders in the /home partition of the original distro.

I currently have 4 separate distros on my computer and all of them share the data folders of my main and original Ubuntu 10.04 with links to each other's home folder.  No configuration files or folders are shared.

I don't have a 64 bit machine to worry about so can not comment on the problems that might arise from that.

---

