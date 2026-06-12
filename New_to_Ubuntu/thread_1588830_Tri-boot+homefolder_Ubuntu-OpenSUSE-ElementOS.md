---
title: "Tri-boot+homefolder| Ubuntu-OpenSUSE-ElementOS"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by TheGuyBehindTheGuy on 2010-10-05
I have a gateway laptop with w7 and an external harddrive that I wish to put Ubuntu Element and SUSE onto with Ubuntu as the main partition. The trouble is, idk how. I have successfully installed each of them solo but cannot figure out how to install them all onto the same HD. Also, I heard that a /home partition is a good idea and would like to include that into the equation. Any help would be nice :)

---

### Post by oldfred on 2010-10-05
You have to plan your partitions in advance and use manual install to choose which partition to use for what. Of course I planned ahead and created a bunch of partitions, some data & some for systems. Unfortunately I did not use paper and pencil to remember which was which and installed a beta install to my data partition. One reason to have good backups:).

You need at least two system partitions. If you want separate /home you will need two more for /home and swap of 2GB or your RAM size. Instead of a separate /home(s), I might suggest a /data partition so you can mount the same data in every install and perhaps another NTFS data partition for any info you might want to share with windows.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by TheGuyBehindTheGuy on 2010-10-05
So /data partitions are for all data and /home partitions are for?

---

### Post by oldfred on 2010-10-05
/home normally has all your data but also all the user settings and configuration files for applications. 

I keep /home as just the (hidden with .) configs and some misc files. Even some data that normally would be in hidden files like my firefox profile, thunderbird profile, and several other programs that I have data in, I move to a folder in my /data partition. This way I can access all my data from any system I start.

---

### Post by TheGuyBehindTheGuy on 2010-10-05
Ok, so I read everything you put. I still have a few questions though.
1. What are going to be the four main partitions (primary)
2. What should be the Logical/extended partitions?
3. How do I make a logical partition?
4. In which order should I install the OS's?
5. Should I partition before with gparted? If so, how?

---

### Post by oldfred on 2010-10-05
You use gparted to create partitions. I would use the three primary and then make the last primary the extended with most of the space. Then you create logical partitions in the extended partition.

You can install in any order, but if you install the one you want to normally boot its install of grub to the MBR will be last and then the default. Otherwise you may have to reinstall grub to the MBR which is no big deal once you have done it once or twice.

If you have created partitions in advance then you use the manual install and choose which partition is / (root) and its format, if you have /home you also choose it, it does find the swap on its own.

Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

1. 20-25 GB Mountpoint / primary beginning ext4(or ext3) for each system you may want to install
2. all but 2 GB (or RAM size) Mountpoint /home  or /data logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory) at end of drive

---

### Post by TheGuyBehindTheGuy on 2010-10-05
Ok, so where does each /boot go? Is /data a primary, extended, or logical? 
(btw thanks for all the help so far)

Edit: oh, and how do I create a /data partition?
Edit2: Where do the bootloaders go?

---

### Post by oldfred on 2010-10-05
You do not need any separate partitions for /boot or any other system partition unless you have a server or a very old system that requires /boot at the beginning of the drive. If you do create /boot you have to have one for every system you install as each will overwrite the other if you only have one.

/data can be logical or primary depending on how you plan your partitions. Extended is the one primary that is just a container for all the logical partitions. Only windows (and maybe a few others) has to be installed to a primary partition, but a second copy of windows and all data partitions can be read if in a logical partition.

Whichever system you want as the default has to have its boot loader in the MBR of  the drive. If you have more than one drive you can put different boot loaders in each drive. I have three drives and four systems but each drive can boot a system from the MBR to that drive. Grub normally defaults to sda unless you sepecify otherwise.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

---

### Post by TheGuyBehindTheGuy on 2010-10-06
I'm still having trouble creating a /data partition. I have gone through all of the installations except ubuntu and still cannot figure out how to make a /data. I have about 100gb towards it and i right clicked on it (in ubuntu installation) and set it to EXT4 but could not find /data for the mount point. Where is it?

---

### Post by oldfred on 2010-10-06
I always create partitions with gparted in advance, so I do not see your problem, but /data is not a standard system partition and you can actually call it anything. Just leave the space unallocated during the install and then you can create it after you boot the install. Gparted is not installed as you cannot edit mounted partitions but I download it just to review things and since I have unmounted partitions I can use it for that. Or use the liveCD. I also like to label partitions which you can do in gparted or with disk utility after you are done.

---

### Post by TheGuyBehindTheGuy on 2010-10-06
Well, firstly I thank you for helping me. Everything is running perfectly. I have no idea if the data partition works or not but will know shortly. Thanks! =D>

---

### Post by oldfred on 2010-10-06
Ok, Some more info:

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions. Not for NTFS

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

But I now do it more like this comment in this blog:
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
 Morgan Hall said:

My personal solution (yes, I use thunderbird) -- I make my data directory a partion mounted on /usr/local so my homebrew apps are in /usr/local/bin. A data directory there contains the working directories for home data -- /usr/local/morganh/Data

Directories in /usr/local/morganh/Data include Downloads, Video, VirtualBox, mozilla, mozilla-thunderbird and so forth.

I install the new distribution, mount my /usr/local, strip out everything except Desktop from /home/morganh then run:

for i in `echo /usr/local/morganh/Data`;do ln -s $i; done

---

