---
title: "Is it possible to have the home drive mapped to a separate hard-drive ?"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by chamira on 2010-12-10
Still new to Ubuntu so forgive me if I'm asking silly questions.

I would like to map the home drive to a completely separate physical hard-drive (i.e. not a partition on the same drive) to that containing the O/S. Is this possible? 

Would it involve mounting this home hard-drive at boot?

I only ask as this is how I keep my data and O/S & software separate on my Windows - it has worked very well for many years, kept my data safe from O/S hard-drive failure and virus attacks. I also backed up my data drive to an external hard-drive on a weekly basis. A bit paranoid when it comes to stuff I create!

---

### Post by BugBuster on 2010-12-10
Yes it is possible to do so. Its simpler to do if done at the time of installation.
You just have to select the appropriate partition on the desired disk when the installation asks and selecting the mount point as /home

> Would it involve mounting this home hard-drive at boot?
Yes, the home partition has to be mounted for you to be able to login. But nothing has to be done on your part. Ubuntu should do it for you. Also I assume this partition preferably have a linux (ext2/3/4 etc) file system for things like file permissions and ownerships to work.

---

### Post by chamira on 2010-12-10
So it would be easiest if I install, format & partition the new hdd and then re-install Ubuntu and configure the home to the new drive/partition?

Will this gurantee the hdd with home will mount on boot up?

Is there another way without re-installing Ubuntu?

---

### Post by BugBuster on 2010-12-10
> **chamira said:**
> So it would be easiest if I install, format & partition the new hdd and then re-install Ubuntu and configure the home to the new drive/partition?

Will this gurantee the hdd with home will mount on boot up?

Is there another way without re-installing Ubuntu?

I guess the answer to all of your questions is yes. However hang on a moment before rushing to re-installation/partitioning as I am sure there should be a way to relocate the existing home to another disk/partition

Someone better at ubuntu than me should surely be aware of a way to do this;)

---

### Post by amjjawad on 2010-12-10
> **chamira said:**
> Still new to Ubuntu so forgive me if I'm asking silly questions.

I would like to map the home drive to a completely separate physical hard-drive (i.e. not a partition on the same drive) to that containing the O/S. Is this possible? 

Would it involve mounting this home hard-drive at boot?

I only ask as this is how I keep my data and O/S & software separate on my Windows - it has worked very well for many years, kept my data safe from O/S hard-drive failure and virus attacks. I also backed up my data drive to an external hard-drive on a weekly basis. A bit paranoid when it comes to stuff I create!

I may not answer your question directly but there's something you need to understand. Linux is NOT Windows and Windows is NOT Linux :)

I see you're trying to do that in "Windows-Way". I've never heard about that before. You could still keep /home on the same partition where your Ubuntu's root partition exists and do a backup if you need that. After all, again, Ubuntu (Linux) is not like Windows. You don't have to worry that much.

Try to search on Google and see whether users recommend that or not. For me, I don't have to do that but that's my opinion.

Few links might help:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[https://help.ubuntu.com/](https://help.ubuntu.com/)

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by amjjawad on 2010-12-10
> **chamira said:**
> So it would be easiest if I install, format & partition the new hdd and then re-install Ubuntu and configure the home to the new drive/partition?

Will this gurantee the hdd with home will mount on boot up?

Is there another way without re-installing Ubuntu?

Do yourself a favor and install Ubuntu (the whole thing) on a separate HDD.

sda  or HDD1 will be for Windows
sdb or HDD2 will be for Ubuntu.

However, there are many things you need to be careful with. For example:

1) Which OS you want to be the first to boot?
2) What Boot Loader you want to take control over booting the two OS's?
3) Do you want to keep Ubuntu or just trying it for few days?

and so on.

---

### Post by owiknowi on 2010-12-10
Workaround:

Have all my personal files (home directory/folder) on an external disk (Fat32 or NTFS).
It's automatically mounted under both Linux and ms wx.

Downside for linux: I made it my /home partition during installation.
Don't know how to change that after the OS is already installed.
However in most applications you can manually change the path to store your files. 

Downside for ms wx: have to manually correct paths to external disk (tweakui can do this the easy way for My Documents I believe).

---

### Post by amjjawad on 2010-12-10
> **owiknowi said:**
> Workaround:

Have all my personal files (home directory/folder) on an external disk (Fat32 or NTFS).
It's automatically mounted under both Linux and ms wx.

Why the long hard way? as long as he has two Hard Drives, he could install Ubuntu on the 2nd and keep the 1st for Windows.


>  Downside for linux: I made it my /home partition during installation.
Don't know how to change that after the OS is already installed.
However in most applications you can manually change the path to store your files. 

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by owiknowi on 2010-12-10
> **amjjawad said:**
> 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

There is the easy way!

I use my way because I remove the disk with personal files every night.
So when my computer is stolen, again, they won't have any of my personal data.

---

### Post by thatguruguy on 2010-12-10
I kinda like the idea of having /home on a separate disk.

---

### Post by amjjawad on 2010-12-10
> **owiknowi said:**
> So when my computer is **stolen**, again, they won't have any of my personal data.

Do they steal computers where you live? :D

---

### Post by 3rdalbum on 2010-12-10
You can do this without reinstalling Ubuntu.

First, copy all the data from /home (**not** just /home/username) to the other hard disk, which should be formatted as ext3 or ext4.

Open Disk Utility and determine the device file name of the hard disk partition that your new /home should be on (it will look something like "/dev/sdb").

Open the /etc/fstab file as root:

```
gksudo gedit /etc/fstab
```

Add a line like this:

```
/dev/sdb /home           ext3    defaults        0       2
```

Make sure you substitute "/dev/sdb" for whatever the device file name is of your new hard disk, and "ext3" for "ext4" if you are using Ext4 for the new home.

Reboot and your active home directory will be on the new hard disk. Note that I haven't told you about how to remove the previous /home from your old hard disk - you should probably do this from a live CD once you've determined that all your files copied over to the new disk correctly and that the new /home works as it should.

---

### Post by nothingspecial on 2010-12-10
> **3rdalbum said:**
> Make sure you substitute "/dev/sdb" for whatever the device file name is of your new hard disk

Or better still use the uuid which you can find by typing

```
sudo blkid
```

```
UUID=a12a5de3-eb34-46rg-8ddf-b45377b841ee /home           ext4    defaults        0       2
```

---

### Post by owiknowi on 2010-12-10
> **amjjawad said:**
> Do they steal computers where you live? :D

Well, it's more a kind of a tradition around these parts. Comes with our genes.

Sorry, let's focus on the thread:

If you use ext3 or ext4 you won't be able to access your files from ms wx.
If you use fat32 or NTFS you can access them from both Linux and ms wx.
The latter OS has it's limits or sum such I believe...

---

### Post by conradin on 2010-12-10
Would it server the same functionality to just remount home on a separate location? after boot?  I'll try it later. As long as the folder isnt in use you should be fine.

---

### Post by chamira on 2010-12-10
Thank you everyone for all the advice. 

I didn't mean to confuse anyone with the reference to Windows - My Windows O/S is already on a separate HDD and my so are my Windows data files.

I don't want to mix the two types of files.


What I wanted to do was purely on Ubuntu - mainly because I have an irrational fear of hdd failure. Anyway, I think you have given me several choices. I will try these out and report back on this thread.

I could also just regularly synch my home folder to a folder on another hdd - that would be the simplest and possibly the safest.

---

### Post by amjjawad on 2010-12-10
> **chamira said:**
> My Windows O/S is already on a separate HDD and my so are my Windows data files.

>  I don't want to mix the two types of files.


That's exactly why I suggested to install Ubuntu on a different HDD.

As for backup, you're already using external HDD, right? in that case, you don't really need to worry about anything.
Installing Ubuntu is much faster than Installing Windows, that in case you need to re-install it and in most cases, you don't need that :)

GOOD LUCK :)

---

### Post by mlentink on 2010-12-10
> **owiknowi said:**
> If you use ext3 or ext4 you won't be able to access your files from ms wx.
not true, you could use [www.fs-driver.org]("http://www.fs-driver.org") works fine
> **chamira said:**
> I don't want to mix the two types of files.

For which you're likely to have your reasons. But I use a common Ubuntu/Windows /home partition (ext3) on my netbook which makes sure I don't have to do separate backups for windows and ubuntu. I only backup that common partition.

---

### Post by owiknowi on 2010-12-10
[QUOTE=mlentink;10223466]
not true, you could use [www.fs-driver.org]("http://www.fs-driver.org") works fine

To be true or not to be true, that's not the quite the issue.

Anyway, still a nice tip!

On the website however I found that ext2 is supported, latest ver. 10-27-2008.
Q: this means ext3 and ext4 are supported as well?

Addendum for chamira:
When using fat32 take it's file size limitation (4GB) in consideration.
To be sure: [http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)

---

### Post by oldfred on 2010-12-10
I have a few rules but have never actually written them down.

Keep systems separate from Data.
Keep an entire system on a drive so the drive can boot even if other drives fail.
Do not write into another systems partition unless you have to to make repairs. Reading is ok or mount windows system partition as read only.
Even in Data partitions use reliable drivers. i.e. NTFS driver in Linux is now considered reliable enough to read data partitions. Do not use FAT32 unless other device - camera, xbox, etc have to have it. And not for large partitions.

For new users I usually suggest a separate /home as that keeps the system & data separate, but user data is in /home and it is required to boot. So I would keep it on same drive.

If using separate /data and/or /shared for data keep /home in the / (root) partition as it will mostly have hidden files & folders and is easy to back up as it is relatively small.

Backup to external devices regularly and to other drives frequently.

---

### Post by nothingspecial on 2010-12-10
I don`t even have my data (as in photos, music, secret plans for to take over parliment etc) on the computers I use (on my lan).

That`s on my "server"

Which backs up to another box upstairs, which has a completely different electric circuity thing. (unlikely to short at the same time).

I just mount it all with sshfs.

---

