---
title: "Is there a formula for how to partition a hard drive?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by klemperal on 2009-12-28
Ubuntu must use some sort of mathematical formula when it automatically partitions your hard drive during the install process (assuming you choose not to do this manually).  I am wondering what that formula is--i.e. X% of total disk space goes to the root partition and X% of the total space goes to the home partition etc.  If you don't know Ubuntu's formula, is there simply a generic one that you go by?  In either case, please be as complete as possible in you answer (i.e., X% of HD should go to home, X% of HD should go to root etc.)

Thanks in advance,
klemperal

---

### Post by lavinog on 2009-12-28
I thought it just makes a swap partition and uses the rest for the root partition (with home included in the root.)

---

### Post by TheNosh on 2009-12-28
i didn't think the default had a separate home partition and root partition? isn't it just the single partition for the whole operating system and then something like RAM x 2.5 for swap?

as for how it decides how much to leave for windows (if you chose to leave windows on the drive) i don't recall.

---

### Post by natravis on 2009-12-28
The default ubuntu install will only create an "Ubuntu" partition and a swap partition. If you want to partition out your hard drive, what I usually do is give about 2GB for swap (though with 4GB of RAM I almost never touch it), 10GB for "Ubuntu" and the rest for "/home" as that is where all my data is stored (movies, music, downloads and of course, your programs settings). I don't recall if the installer lets you say "make this partition at the end of the disk" but if not, just do some simple math to figure out how big your harddrive is in MB (use google converter) and subtract 12,288 from that number to make your first partition (/home), then approx 10,240 for /, then all remaining for swap.

---

### Post by klemperal on 2009-12-28
So the "Ubuntu" partition is just one big root partition?  Could I partition other distros this way as well?

---

### Post by natravis on 2009-12-28
> **klemperal said:**
> So the "Ubuntu" partition is just one big root partition?  Could I partition other distros this way as well?

You could say that. The ubuntu partition will hold all the stuff it is supposed to have, unless you specifically mount it elsewhere (like /home on a separate partition). Other distros should be similar but I do not have enough experience to say it would be exactly the same

---

### Post by klemperal on 2009-12-28
> **natravis said:**
> You could say that. The ubuntu partition will hold all the stuff it is supposed to have, unless you specifically mount it elsewhere (like /home on a separate partition). Other distros should be similar but I do not have enough experience to say it would be exactly the same

Ah, I think I understand.  So, instead of having separate mount points for separate partitions, you have separate mount points on one big partition?

---

### Post by adam814 on 2009-12-28
No, it's all the same partition.  This doesn't make /home a mount point, just a folder.  You can't umount /home since it's not a partition.

You might be thinking of an LVM setup where one or more physical devices/partitions form a volume group where you can create individual logical volumes (which function as partitions but are more easily movable and resizable).

I'd strongly recommend using a separate home partition.  Among the benefits are that you can always reinstall your distro without formatting your /home partition so you don't need to back up files in it to do a fresh install of a different distro or new version.

Also if you use more than one distro you can (so I've heard) use the same /home partition for both assuming they use close enough versions of the same apps.

---

### Post by natravis on 2009-12-28
> **klemperal said:**
> Ah, I think I understand.  So, instead of having separate mount points for separate partitions, you have separate mount points on one big partition?

Not exactly. If you want a particular "folder" to be on a different partition, you would specify that while installing. For example, people with SSD drives can do some crazy partioning to get awesome performance from their drives while standard 7200RPM or so drives dont need nearly so much tweaking. My hard drive looks like this:
```

Win7    Shared Data   ["/home"  "/"     Swap]
30GB       33GB        36GB     11GB     2GB
```

[]=extended partition

Most people use a separate /home partition to make clean upgrades easier or for easy backup, at least to my knowledge (and personal experience).

---

### Post by Chris Edgell on 2009-12-28
I wonder if this would be something you'd like to read.  I liked it.

 Re: Partitions
This may or may not pertain, if it doesn't, please let me know. I have run across this description of partitions written by JKyleOKC:

"Think of your hard drive as a big box that has a number of smaller boxes in it (the partitions). Its name is "sda" and the file system addresses it as "/dev/sda" without a number. The partitions are numbered: sda1 and so on, and addressed as "/dev/sda1" et cetera.

The letters (a, b, c, d) are assigned according to the connectors on the motherboard and the numbers according to the sequence of entries in the drive's partition table (an area at the start of the drive that tells where the data is located). This table has room for only four entries, which will be sda1 through sda4. To get more partitions, one of the four has to be an "extended" partition, which is another box full of partitions such as your sda5, 6, 7, and 8. You don't need to worry about these because the partition manager will take care of the details.

To access the contents of a partition, it has to be mounted. The file manager of the live CD normally does this for you, so that you can click on the partition's icon and see the list of directories it contains. One of them will be "home" and inside that directory will be at least one more, bearing your user name. That inner directory is the one you want to back up.

If the file manager does not show you icons for the partitions, you'll need to "mount" them to gain access. However let's not try to cross that bridge until it becomes necessary, since it can be a bit confusing at first! Tools are available to simplify it, fortunately.

With a little experience you'll find this stuff much easier to get along with; it's all pretty logical, just different from the systems that you're used to!"

---

