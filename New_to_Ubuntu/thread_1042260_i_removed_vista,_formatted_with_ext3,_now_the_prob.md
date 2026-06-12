---
title: "i removed vista, formatted with ext3, now the problem is"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by fuser312 on 2009-01-17
the newly formatted space is placed in /media only, can't i use this space in /home directory. is it possible??

can't i use this space in / only.
i am real low in term of space in ubuntu, and i fear i might ran out of the space in / directory,  if i do ran out of the space there, where will synaptic install new packages??

please clear my doubts

---

### Post by earthpigg on 2009-01-17
can you clarify your situation and objectives, please?

---

### Post by seagullplayer77 on 2009-01-17
Yeah, I'm not quite clear on what the problem is here either.

It sounds like you're running out of room on your / partition, and that the only other space you have is formatted as you /media partition. Is that accurate?

If that's the case, then I'm not sure you'd be able to merge the /media partition with the one that's formatted as /. I don't think that's possible...sorry to disappoint.

---

### Post by fuser312 on 2009-01-17
i am able to use that space through /media but i want to use that space in /home or 
i am so confused right know.

ok look at this, if i do ran out of space in my / directory i.e. /usr/bin too. where will my newly installed softwares from synaptic will go. isn't there any way to get more space in thoose directories

---

### Post by jimmy the saint on 2009-01-17
If what you want to do is make more room for your home directory, there are two things you can do.  First, though, the reason it is showing up in the media directory is that Ubuntu mounts all extra drives/partitions there.  

The easiest thing you could do would be to add a symlink in your home directory to that partiton.  By doing so, you will get a "folder" in your home directory that links directly to that partition.  You can just put stuff in there like you would any other folder in your home directory.  I will include a link to some community documentation as well as the relevant text.
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

> More technical tips

Symlinking for greater convenience

If navigating to a partition's mount point seems inconvenient, even with the links on the left of Gnome's file browser, a link can be placed on the desktop, or anywhere else, for that matter.

Try the following command.

ln -s /media/windows ~/Desktop/

A link to the directory '/media/windows' will be placed on the desktop. Files may be dragged into it, it may be opened, it can be renamed and moved, and if it proves to be annoying, it can be deleted like any other file without risking damage to its contents.

This process is called symlinking because the link created is symbolic. It merely points to the location being referenced. 

Be aware that the first folder in the command is the partition you want to link to and the second folder in the command would be your home directory, rather than your desktop.

If you really want to do it right, read the info on setting the partition to mount automatically.  You can create a folder in your home directory to which that partition will automatically mount at every boot.  The symlink will do essentially the same thing but a lot easier.

Good Luck

---

### Post by fuser312 on 2009-01-17
what about if i need more space for installation of softwares, updates etc. i am running out of space for that.

---

### Post by jakupl on 2009-01-17
No. If you only have a single partition for ubuntu. That is, you don't have a seperate /home partition, then you should just boot with the ubuntu cd, enter gparted "System --> Administration --> Partition Manager",

In there you can erase the useless partiton and expand your ubuntu partition to fill out the newly freed space.

WARNING!!!!
Although I personally have never experienced any problems while partitioning, I feel obliged to tell you, that it is best to always backup your stuff before partitioning and editing partitions. It is always risky. e.g. if there is a power shortage while you are partitioning or something.

---

### Post by ugm6hr on 2009-01-17
Is this a partition on your main HD?

If yes - you could potentially resize / move partitions to make it 1 partition.

Another option is to make the newly formatted partition a separate /home partition.

Read here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

But you can't just use a different partition as /

---

### Post by fuser312 on 2009-01-17
hey jackupl, are you sure i can just expand my exisying partition using gparted? can you give me a link or name to search in synaptic to install some good back up software for ubuntu

i am not trying to create a different /

---

### Post by jakupl on 2009-01-17
Yes I am sure. I have done it numerous times while playing with partitions. at the momenth I have five partitions. One for /, one for /home, one for /home/username/pictures, one for /home/username/videos, and one for swap.

I would just put all the important stuff on a usb stick, or external hard disc if it takes alot of space. If you are not satisfied by this, you can check these posts:
[Howto: Backup and restore your system!]("http://ubuntuforums.org/showthread.php?t=35087")
[Backing Up in Ubuntu]("http://www.psychocats.net/ubuntu/backup")
[Good Backup Software]("http://ubuntuforums.org/showthread.php?p=2730750")

---

