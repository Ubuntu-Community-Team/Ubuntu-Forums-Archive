---
title: "filesystem root: low disk space warning  !!!!"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2011-02-21
Today for the first time I received a low disk space warning for "filesystem root." 
Attached are two screenshots showing the disk usage.

Total Filesystem Capacity is over 85 gig and there's supposedly 52 gig available.  Why is root out of space?

What are my options?

Boot Live CD and use Gparted to make device sda5 larger?


 I thought have a seperate partition for /home (sda6) would keep the other Linux partition freed up except for repository downloads and such. 

Are there any files I can do without in sda5?

---

### Post by mikewhatever on 2011-02-22
Your root partition is 28GB, not 52GB. You can probably free some space by removing unneeded kernels and headers, as well as cached installation files, but that would give you a couple of GBs or so. Can you post the output of the following to show where most of the space is:
```
sudo du -hs /*
```

---

### Post by migrate from windows on 2011-02-22
The best is to boot with live cd and use gparted to move some of the unallocated space to ur root partition ( it has got only1.72 gb left). make sure to click swap off during the process. have done it before its an easy process.

---

### Post by ozark_hillbilly on 2011-02-22
Mike,  Here's the output:


ed@ed-desktop:~$ sudo du -hs /*
[sudo] password for ed: 
6.6M	/bin
46M	/boot
4.0K	/cdrom
564K	/dev
15M	/etc
du: cannot access `/home/ed/.gvfs': Permission denied
du: cannot access `/home/cindy/.gvfs': Permission denied
6.9G	/home
0	/initrd.img
0	/initrd.img.old
334M	/lib
16K	/lost+found
13G	/media
4.0K	/mnt
93M	/opt
du: cannot access `/proc/6523/task/6523/fd/3': No such file or directory
du: cannot access `/proc/6523/task/6523/fdinfo/3': No such file or directory
du: cannot access `/proc/6523/fd/3': No such file or directory
du: cannot access `/proc/6523/fdinfo/3': No such file or directory
0	/proc
8.7G	/root
6.6M	/sbin
4.0K	/selinux
200K	/srv
0	/sys
132K	/tmp
2.6G	/usr
612M	/var
0	/vmlinuz
0	/vmlinuz.old
ed@ed-desktop:~$

---

### Post by mikewhatever on 2011-02-23
Ok, thanks for the output. There are two locations to check, **8.7G /root**, and **13G /media**. Something takes way too much space in those dirs.

---

### Post by ozark_hillbilly on 2011-02-23
Mike,

Found almost 6 gig in root/.local/share/Trash/files

I assume it is OK to delete the files under /Trash/files ?????

See screenshot attached....

It seems when I delete these files it recreates them ????? 2.2 then 2.2.2 and son on as I try to delete them.
They were old files I was transferring when repartitioning back when upgrading to 10.04....

Confused as to why they regenerate these files....

---

### Post by mikewhatever on 2011-02-23
It seems like you don't really delete files, but rather move them to Trash. Use Shift+del to avoid that. Personal files are usually not owned by root, so you likely didn't have to be root to delete them.

---

### Post by ozark_hillbilly on 2011-02-23
So to be clear then is it OK to remove the files in root/.local/share/Trash/files as long as I don't want or have a need for them?

Because I noticed when I empty my Trash can those particular files are not erased.

---

### Post by drs305 on 2011-02-23
Your trash is separate from root's trash. You can empty your normal Trash Bin but to clear the contents of root's trash you have to use root privileges. You can open Nautilus as root or use the command line (root Nautilus is safer). With Nautilus, as you have been instructed, you have to use SHIFT-DEL or the files will just recycle back to the Trash Bin.

One way to open a folder as root is to install *nautilus-gksu*, which allows you to right click on a folder and open it as 'root'.

---

### Post by ozark_hillbilly on 2011-02-23
Thanks for the clarification drs.
Not to belabour the point but why does root have a Trash area? And why do the files just pile up in it? Is this an area were supposed to monitor and delete periodically? 
As an old gray haired newbie I didn't even realize root was throwing Trash into it's own "receptacle."  :^ )

ed


p.s.    i now have over 10 gig free space in root so some breathing room has been established..... 

thanks Mike and drs !!!

---

### Post by drs305 on 2011-02-24
Think of root as a separate user. When you are logged in as root or using admin privileges and files are deleted, the deletions belong to root, As a multiuser system, the OS wouldn't just throw trash into some other user's trash bin. The trash belongs to the user who deletes it and goes into the applicable trash bin. A normal user cannot delete things owned by root without invoking admin privileges, so when you use 'sudo' or 'gksu', for purposes of trash, you become 'root'.

You could make an argument that if there is a single user the trash should go to a single trash bin, to which I would respond - I didn't design the system.  ;-)

So, the things that are owned by root and that you as a normal user with admin privileges might need to keep an eye on include:
Large or numerous log files. These accumulate in the /var/log folder, are owned by root, and are automatically kept to a reasonable number and size. If something goes wrong, these files could end up occupying a huge amount of space.

Downloaded packages: Again, there are settings which detemine how large and how long downloaded packages remain in /var/cache/apt/archives. You can change the default settings or remove all the accumulated .deb files, which are not needed after installation, with "sudo apt-get clean".

And Trash....    ](*,)

Happy Ubuntuing.

---

### Post by BorisPlankton on 2011-03-05
Hi,
I have the same warning. I have output from du -hs /* as:
=========================================================================
7.8M	/bin
95M	/boot
4.0K	/cdrom
572K	/dev
15M	/etc
du: cannot access `/home/boris/.gvfs': Permission denied
117G	/home
0	/initrd.img
0	/initrd.img.old
570M	/lib
7.6M	/lib32
0	/lib64
16K	/lost+found
8.0K	/media
4.0K	/mnt
4.0K	/opt
du: cannot access `/proc/2656/task/2656/fd/4': No such file or directory
du: cannot access `/proc/2656/task/2656/fdinfo/4': No such file or directory
du: cannot access `/proc/2656/fd/4': No such file or directory
du: cannot access `/proc/2656/fdinfo/4': No such file or directory
0	/proc
164K	/root
8.4M	/sbin
4.0K	/selinux
4.0K	/srv
0	/sys
64K	/tmp
6.6G	/usr
1.1G	/var
0	/vmlinuz
0	/vmlinuz.old
========================================================================

Looks like home folder and I might need to resize using live CD and gparted?  I have plenty of room on hard drive and do not want to thin home folder. 
Bit puzzled as I had thought I had set up with a seperate pertition for my home folder but is seems not?

---

### Post by mick8985 on 2011-03-05
Boris you need to think about how you are organising your storage.
How big the the drive? resizing more space for you root filesystem which your home is stored on will only by you so much time before you fill it again.
I'd consider buying a bigger drive and use it solely for /home/,
At the very least you should give home it's own partition seperate from /

---

### Post by BorisPlankton on 2011-03-06
Hi thanks Mick 8985.
Hard drive is 500 Gb.
Having run Gparted to look at my partitions I think home does have it's own partition and is sized at around 450Gb (sda6). Root is 9.31 Gb (sda1) with over 1.07Gb free.and swap is just over 2Gb. I have attached screen print to show Gparted picture.
So my space issue must be coming from my root and I need to make this larger using Gparted from installation disk?
Grateful if my reasoning/understanding here could be checked before I go ahead.
Kind Regards and Thanks the assistance.

---

### Post by fabricator4 on 2011-03-06
9 GB is a little tight for the filesystem.  Most of the space is taken up by /usr which is probably installed programs.  Lots of installed programs, probably.

It's perfectly feasible to run a system off a partition of this size - my Asus 900SD only has a 8Gb SSD to work with, and I've got /home on that as well.

At this point you could do one of two things...  Either uninstall some unused and unwanted programs, or increase the size of the partition that the filesystem is on.  If you're going to do this, I recommend you backup up your /home partion first, since you're going to have to make it smaller.

I normally say 30 GB is plenty for the root filesystem on a desktop install, but others may have different ideas.

For now, you could uninstall old kernels and headers, and delete all the installation files (*.deb) in /var/cache/apt/archives.  That will only get you a GB or so however.

Chris.

---

### Post by BorisPlankton on 2011-03-06
Thanks Fabricator4 backing up home now and then will resize. It seems I was a little light on my root partition size.
Thanks.

---

### Post by BorisPlankton on 2011-03-07
Ok Used Gparted on the live CD and resized /Home (sda6) fine. But I cannot resize root (sda1). Well actually I am able to make smaller in size but I cannot increase over its current size. Can anyone guide me?

---

### Post by fabricator4 on 2011-03-07
> **BorisPlankton said:**
> Ok Used Gparted on the live CD and resized /Home (sda6) fine. But I cannot resize root (sda1). Well actually I am able to make smaller in size but I cannot increase over its current size. Can anyone guide me?

The only thing I can think of is that /home is on an extended partition with the swap file.  You might have shunk the home partition upwards, but the extended partition is still where it was.

In this case you would have to shrink the extended partition upwards as well.  If you're not sure take a screen shot of the Gparted screen and post it here so we can see what's going on.

Chris

(Edit)
I just had a look at your previous screen shot of Gparted. Indeed the swap and the /home partitions are on an extended partition, with the swap file at the beginning.  You'd actually have to do three things here: Shrink the home partions upwards, move the swap partition up to the /home partition, then shrink the extended partition up to the start of the swap partition.

This should leave some unallocated space after the / partition  that you can increase it into.

Chris.

---

### Post by BorisPlankton on 2011-03-13
Chris,
I apologise for slow response. I had worked out what to do by experimentation rather than your solid advice. However I had power cut while using Gparted and could not reboot so re-installed and set my root folder to 30Gb - should keep me safe for while!
Thanks for the help.
Paul

---

### Post by fabricator4 on 2011-03-13
> **BorisPlankton said:**
> Chris,
I apologise for slow response. I had worked out what to do by experimentation rather than your solid advice. However I had power cut while using Gparted and could not reboot so re-installed and set my root folder to 30Gb - should keep me safe for while!
Thanks for the help.
Paul

Which goes to show that Murphy was actually an optimist.  Glad you got there in the end ;-)

You might mark this thread solved (in "thread tools" above)

Chris

---

