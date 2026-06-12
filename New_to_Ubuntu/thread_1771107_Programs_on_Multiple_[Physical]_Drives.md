---
title: "Programs on Multiple [Physical] Drives"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by Depravitus on 2011-05-30
Hey everyone,

*Very excited* to find 11.04 live recently and decided to try switching fully over to it again (hard for a graphics designer/gamer!) I enjoyed 10.10 quite a bit, but found it hard to give up Cinema 4D in lieu of Blender at the time.

Anyway, to the topic at hand... I have become accustomed to having my OS on my SSD boot drive, with core applications on it (photo editing, 3d software, etc) and "non-essential" applications on an external drive with much more space to spare.

Is this something I can cleanly do with Notty? The only related procedures I have found involve moving the entire Home folder to the external drive, which severely lessens the benefits of an SSD in my situation.

I have the same question in regards to documents... I keep my project files on a RAID1 configuration, and all other media on the same drive that handles "non-essential" programs. Again, the SSD is just meant to handle my OS and my work related software.

Thank you for reading.

---

### Post by humzayunas on 2011-05-30
HOw to install multiple programs on the ubuntu i am having trouble with installation

---

### Post by Hugh971 on 2011-05-30
You can use LVM to do that. That basically allows you to spread the filesystem (/) across multiple physical disks. 

I think you can do it while your installing by specifying partitions manually.

---

### Post by Paqman on 2011-05-30
> **Depravitus said:**
> 
Anyway, to the topic at hand... I have become accustomed to having my OS on my SSD boot drive, with core applications on it (photo editing, 3d software, etc) and "non-essential" applications on an external drive with much more space to spare.

Is this something I can cleanly do with Notty? The only related procedures I have found involve moving the entire Home folder to the external drive, which severely lessens the benefits of an SSD in my situation.

If you specify "advanced partitioning" during installation you can put any part of the filesystem you want onto any particular partition. So yes, you could move as much as you want onto whatever drive.

However, applications don't simply install into one location. Settings, config and data will be in /home, the executable could be somewhere like /usr, etc, etc. Unless you have a lot of particularly massive executables then i'd say keeping all but /home on your SSD is the way to go. Space won't be an issue. I have a separate / and /home, and my / only takes up 4.6GB of the 16.6GB i've given it, so unless you've got a teeny weeny SSD then it's plenty big enough. Linux is not Windows, you won't need masses of room for installed apps. Your home folder will be much bigger than /. Mine is 10.6GB, which does include Windows apps installed through Wine, but not really much data.

> 
I have the same question in regards to documents... I keep my project files on a RAID1 configuration, and all other media on the same drive that handles "non-essential" programs. Again, the SSD is just meant to handle my OS and my work related software.


Again, very similar to me. All my data is on a RAID1 NAS on my network, I don't store anything on machine and use an SSD. If your RAID array is a Windows network share you'll want to add the shared folders to [/etc/fstab]("http://ubuntuforums.org/showthread.php?t=288534") to make things nice and seamless.

---

### Post by Depravitus on 2011-05-30
> **Paqman said:**
> [snip]


Thanks Paqman, very informative post.

I do have a question about 'executables' being on the external and program data remaining in Home, though. 

Lets take Rift Live for instance, it's a game that is currently about 10 gigs in size and will likely bloat up to as much as 20. Having come from Window$, I understand 'executables' to simply be the small ~1-5 mb launch files that are used to initiate program data. Is that 'catalyst' the only thing stored on the external partition/drive?

With that said, again I have come from Window$ so advanced partitioning in Ubuntu is somewhat beyond me. Could you perhaps explain to me what I need to do with the Mount Points and sundry in my particular circumstance? 

1.5tb - dedicated to Media and "non-essential" software
500gb RAID1 - dedicated to documents
64gb SSD - OS drive and essential software

Apologies for the amateur questions. I greatly prefer 'nix workflow and configuration options, but it definitely means training myself to think differently with my OS.

---

