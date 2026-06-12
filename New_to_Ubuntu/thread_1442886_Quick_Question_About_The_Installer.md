---
title: "Quick Question About The Installer"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by TheGreenSparrow on 2010-03-30
Hi,

I'm new to Ubuntu and I just have a small (and I suspect, relatively easy) question that I'm guessing most of you can help with.

I have Windows 7 pre-installed on my machine, so it has two partitions already created (the OS and the OS recovery sections). When I reach the partitioning section of the Ubuntu (9.10) installation, and choose to create another partition (co-existing with Windows) it lists two extra hard drive partitions that it would add; "dev/sda3" and one just called "Ubuntu 9.10".

My question regarding this is, which of those needs to be bigger, and what is the exact difference between them? Is one a swap section and the other just for the installation files and the main OS? I just want to make sure before I install anything.

I have a 320 GB hard drive, and I intend to use 170 GB for Windows and the remaining 150 GB for Ubuntu. So if one of those is the swap partition and the other contains just the main files, how much should be enough to allocate just to the latter? I've read 10 GB should be enough, but when the installer automatically adjusts the sizes, they seem to be equal, each being somewhere around 120 GB.


Another question, completely unrelated; I have 4 GB of RAM and a 64-bit processor. Should the 64-bit version of Ubuntu work without any problems, or should I rather install the 32-bit version for stability? I've noticed on some other distro websites, they've recommended 32-bit over 64 for stability, but is that an issue with Ubuntu as well?


Thanks in advance for any help. It's much appreciated.

---

### Post by rockerphil on 2010-03-30
ok, here's a quick run down. it's really up to you on how big you want to make the partitions, but you've basically got it right, one partition holds the root file system of the Ubuntu OS and the other is for swap, which is a lot like the Windows paging file, except it's on it's own partition. as far as 10 GB of swap goes i wouldn't recommend it. it's like having a house with 100 rooms, you'll probably never use em all. if i remember correctly (somebody please correct me if i'm wrong) it's suggested to make your swap partition 1/2 the amount of your RAM. so if you've got 4 GB of RAM then 2 GB of swap should suffice. as far as the 32 bit versus 64 bit thing goes i can't say from personal experience, but from what i've heard (again someone please correct me if i'm wrong) you really don't need the 64 bit edition unless you're running more than 4 GB of RAM since the 64 bit version has been known to cause more headaches than necessary. hope this helps,

Phil

---

### Post by TheGreenSparrow on 2010-03-30
Thanks. That does help quite a bit.

My only other question is, which is the swap partition: *dev/sda3* or *Ubuntu 9.10*? I'm guessing it's *dev/sda3*, but I don't want to get them mixed up (as I'm sure you can already guess, haha).

---

### Post by J V on 2010-03-30
the swap partition is /dev/sda3... but thats not what you think it is ;)

The swap partition is the vram, you only need 2 gigs of this, the ubuntu core also only needs 10 gigs, what people suggest is making an extra *home* partition and giving that the rest of the space, I have pre-made post here:

> By carefully choosing your partitioning when installing Ubuntu, you can speed up your hard drives, and even let you keep your files and settings with a fresh install!

**Definitions**
HD: Hard-drive, the part of the computer that saves your stuff
File-system: A way to save data, Ubuntu uses the ext4 file-system now
Partition: A "Section" on the HD, it has its own file-system, and can contain files and folders
Format: The action of creating partitions
Mount: The action of loading a partition to be used
Primary: A partition directly on the HD, there are a maximum of 4 of these
Extended: A partition that can hold a number of logical partitions
Logical: A partition "Inside" an extended partition, there can be a lot of these!

Seeing as windows **has** to be installed on a primary partition, you should install Linux in an extended partition, to leave space for unexpected guests.

**Separate home**
Lots of people will talk about a "home partition" or a "separate home" - This is because all of their /home folder is on a separate partition.

This is a fundamental addition to any Linux box, as it lets you install a new version without losing your settings and files.

Another great reason to have a separate home is to run more than one linux distribution. If you are running Fedora and Ubuntu at the same time for example, you can tell them both to run the same home partition, meaning all your settings and files will be cross-OS.

There are other folders some suggest you should separate, but in Ubuntu you can easily create a script that will install all your applications for you, making this irrelevant (And dangerous if you are using outdated apps!)

**Size**
Partitions take longer to mount when they are large, so an ideal partition setup uses smaller partitions.

A swap partition is extra memory for when your ram runs out. Its really up to you, but nowadays its more irrelevant because computers have so much ram... The twice your ram phrase doesn't apply any more.

Greenwidth notes that as of kernel 2.6, a swap file is just as fast as a swap partition, so you may want to leave out the partition and use a file in your root partition instead, which is easier to delete and resize.

audiomick notes that you need a swap partition (not file) equal to or larger than your memory in use to hibernate. so if you expect all 2 gigs ram and some swap to be in use every time you hibernate, you need a swap of 2.5 gigs or so.

2 gigs should be fine for most computers.

The root partition (Everything but the home partition) is about 10 gigs here, but even with lots of apps installed, it only uses 4.1 gigs. 10 gigs should be plenty for all your needs.

The home partition: This ones tricky. Lots of people make their home partition as big as all the space they have left over, but this takes a long time to mount.

Nothing you have will take up that kind of space, give your home about 10 gigs per (active) user, that should be plenty.

Then you create a data partition to keep all the rest of your stuff, so that large files like videos can be stored, but you still get to shave those necessary seconds off your boot time.

**Position**
You computer can be sped up by positioning and sizing the partitions correctly.

The closer a partition is to the heads, the less they have to travel, so the earlier a partition is in the partition table, the faster it will perform.

For this reason I suggest putting the partitions in the following order:


[LIST=1]
[*]Swap (If you are using it)
[*]Root
[*]Home
[*]Data
[/LIST]

Note: If you have an SSD, you can get a HUGE performance boost by installing swap and root on the SSD and using a normal HD for home and data.

**So how do I do it?**
When you are installing, you will come to an option to choose where you want Ubuntu installed on your HD.

Choose "Specify partitions manually"

You will be brought to a special window, where you can edit your partitions to your hearts desire.
[B]
[SIZE=1]** Skip ahead if you don't want to keep your other OS (or don't have one) **[/SIZE][/B]


[LIST]
[*]You might want to perform these actions from the other OS itsself to prevent potential data loss.
[*]Right-click the partitions from the other OS, and click *Resize/move*
[*] Resize the partitions towards the end of the partition, so as to give Ubuntu a faster part of the HD to deal with.
[*] If there are already 4 primary partitions, and none of them is extended, you will have to delete one of them, this is up to you, I don't know which partitions are important on your computer.
[/LIST]

    [SIZE=1]**** Stop skipping now! ****[/SIZE]

[SIZE=1]**If you have an SSD switch to it now (upper right)**[/SIZE]
 

[LIST]
[*]Right-click the empty space, and click NEW
[*] Create an extended partition if there is none, leave room for the following.
[*] Create a swap partition if you want it, if you don't, skip this line.
[*] Next, create an EXT4 partition and select to mount it at / (root), make it 10 gigs (at your discretion)
[/LIST]

[SIZE=1]**If you have an SSD, switch to your HD, create another extended partition and continue**[/SIZE]


[LIST]
[*] Next, create an EXT4 partition and select to mount it at /home, again, your discretion.
[*] Finally, if you don't need the space for something else, create a final EXT4 partition, don't mount it, and take up all the space. This is your data partition.
[*] If you wanted a swap file rather than a swap partition, you just create a file of a specific size on your HD:
```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=<megabytes>
sudo mkswap /swapfile
sudo swapon /swapfile
echo "/swapfile swap swap defaults 0 0" | sudo tee -a /etc/fstab
```
[/LIST]

 Congratulations, you now understand partitioning and have a leaner meaner possibly greener machiner!...

**Separate home partition on machine already installed**
To make a separate home partition post-install, you will need to have an Ubuntu live disc (Or similar live disc with partition editing software)

First of all, backup your home folder (This could get messy with a dodgy HD), you can do this by simply pressing ctrl-h (to show hidden files) ctrl-a (to select everything) and right-click > compress. Then send this somewhere safe (USB, other HD, something off this HD)

Once you have booted up, go to System > Administration > Gparted: This is essentially the same program you encountered during the installation.

Your first action will be to shrink an existing partition to make way for the home partition, I suggest shrinking the root partition first.

Next, create an EXT4 partition in the empty space. Click the apply button to save changes. Right-click it and select information, note the UUID field, we will need it later.

Now, mount the root partition, and the new partition, and note their locations in the live file-system. Execute these commands (Making appropriate changes):
```
sudo mv /mnt/<rootPartitionFolder>/home/* /mnt/<newPartitionFolder>
sudo rm -rf /mnt/<rootPartitionFolder>/home/*
echo "UUID=<uuidHere> /home ext4 defaults 0 2" | sudo tee -a /mnt/<rootPartitionFolder>/etc/fstab
```Shrink your root partition to 10 gigs or so, fill in the space with whatever you want (more home?), reboot: your computer should boot as normal, only with a new home partition.

_If it doesn't work, don't say I didn't warn you! _

Uncompress your backed up home to its former location, boot a live disc, delete the new partition, resize the root partition, remove the last line from /etc/fstab, and (at your discretion) start again ;)

---

### Post by ajgreeny on 2010-03-30
If I were in your shoes, I would do the following:-

1.  Defrag win7 a couple of times, preferably in safe mode, and with virtual memory settings turned off.  (turn it back on again after installing ubuntu).

2.  Shrink win7 main partition with its own disk management software to the 170GB you want, though I have no idea how to do that in win7.

3.  Check that win7 still boots OK.

4.  Start installation of ubuntu from live CD.  This means you can check that ubuntu will run on your hardware if you have not already checked that out.

5.  When you get to the partitioning section, choose to set your own partitions manually, and in the unallocated space make a new extended partition of all the 150GB

6.   Now in the extended partition choose to make a new partition of 10GB at the start of the space, ext4 filesystem with mount point /, (root), and make sure the box to "format" it is selected.

7.  Repeat 6, and use all except 4 GB at the end of the extended partition, using ext4 again, and choose the mountpoint /home, and to format.  Now repeat a last time in the 4GB left at the end and set it as swap, which has no mount point.

8.  Continue with the installation to the end, and you will finish with the best overall installation arrangement in my opinion, ie, 10GB root, a large /home partition, and finally a good sized swap partition.

I apologise if this all seems rather long-winded and slow way to do things, but you will see the advantages of this when you come to upgrade to the next version of ubuntu.

---

### Post by TheGreenSparrow on 2010-03-30
That all helps a lot. 

Thanks very much to all of you. I just wanted to make sure how I was supposed to allocate it, and it seems I was very, very wrong in how I was going to go ahead with it. So luckily I did ask. I appreciate the help very much. I'll mark this as solved now.

---

