---
title: "Starting a dual boot system...I think.."
date: 2011-01-14
forum: New to Ubuntu
---

### Post by mikeybinec on 2011-01-14
Ok, I have 1 partition already set for windows, but I have'nt fdisked the remaining 27 gigs yet. If i understand some of the FAQ's posted around here, I need to set this partition as a FAT32? Do I make this partition a primary or extended? Then install Ubuntu in this partition in what specific manner.. ? as an aside, i can screw this up if I need to and I can reinstall, it does'nt have any important files on the windows side so if I hose the ubuntu section I can start over again.. My aim is to work on the Ubuntu server softwarem but I do want a functioning windows side as I am a Cisco network dude and I configure switches and routers.
 
Thanks for any and all advice.

---

### Post by Paqman on 2011-01-14
> **mikeybinec said:**
> If i understand some of the FAQ's posted around here, I need to set this partition as a FAT32?


You don't need to do anything. Ubuntu can create new partitions and format them for you during installation. It can either create them out of free space, or it can shrink existing partitions. You can either tell it to do this automatically for you, or alternatively you can do manual partitioning where you have full control over what gets created. If you choose the latter Ubuntu will need at least one EXT4 partition of about 10-20GB and a swap partition that should be about 1GB (or equal to the size of your RAM if you want to use hibernation). Installing inside an extended partition gives you extra flexibility in the future. Linux has no problem booting and running from inside extended partitions.

Ubuntu will use Linux filesystems, normally EXT4. FAT32 is a nasty old Microsoft filesystem that should be consigned to the dustbin of history. Its only saving grace is universal compatibility, which is why people used to recommend it for shared data partitions. These days Linux can read and write to NTFS partitions, so the only reason to use FAT32 for shared data would be if you had a Hackintosh installed on your machine.

---

### Post by garyed on 2011-01-14
If you've got the partition sized the way you want for windows it would be easiest to just install windows first & let Ubuntu set up the next partition when you install it. Just make sure you're not using the windows partition for the Ubuntu install.

---

### Post by mikeybinec on 2011-01-15
OK, so how about this:  I have the windows section already set up. I re boot and boot off the ubuntu cd and let it set up the remaining 27 gig section that isn't fdisked yet. And have it set the partition as ext3?
 
OK?

---

### Post by mastablasta on 2011-01-15
if you plan to instal 10.04 it is very easy. you just leave the disk (27) GB unformated and then during instalation you choose to install to largest free disk space. That will install ubuntu to those 27 GB (it will be partitioned automaticly for you). During install linux will detect windows and when you reboot you should have a boot screen where you select the operating system.

10.10 has some bugs during install, so i dont' think this way is a good way on that version :-)

aslo since you are cisco network dude, wouldn't it be more logical to use linux only? why you need windows? I mean afterall linux has it's roots in servers and a lot of routers, modems switches actually use linux as their OS.

---

### Post by Paqman on 2011-01-15
> **mikeybinec said:**
> OK, so how about this:  I have the windows section already set up. I re boot and boot off the ubuntu cd and let it set up the remaining 27 gig section that isn't fdisked yet. And have it set the partition as ext3?
 
OK?

Yep. Although the default filesystem is now EXT4. It's an incremental improvement over EXT3.

---

### Post by mikeybinec on 2011-01-15
> **mastablasta said:**
> if you plan to instal 10.04 it is very easy. you just leave the disk (27) GB unformated and then during instalation you choose to install to largest free disk space. That will install ubuntu to those 27 GB (it will be partitioned automaticly for you). During install linux will detect windows and when you reboot you should have a boot screen where you select the operating system.
 
10.10 has some bugs during install, so i dont' think this way is a good way on that version :-)
 
aslo since you are cisco network dude, wouldn't it be more logical to use linux only? why you need windows? I mean afterall linux has it's roots in servers and a lot of routers, modems switches actually use linux as their OS.
 
Yeah you're right about the Cisco ios is kinda linux based. I'm just a fan of TeraTerm, and my real first linux useage was (promise you won't laugh) Puppy linux, a cd bootable and then I took a community college course running and configuring SLES 9
(SUSE linux) I could run a term program in puppy but I'm used to teraterm with all it's functions, and stuff. The Ubuntu server is just that--more practice with a server based
command line function  (li, chmod, etc etc)
 
The server version I d/l'ed is straight from the front page server section of this website.
 
 Once again, thanks all for the quick responses and the back and forth
 
Thanks, Mike   El Cajon

---

