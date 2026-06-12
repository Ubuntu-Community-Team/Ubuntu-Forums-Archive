---
title: "Missing Sata Drive"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-05-06
I had to re-install evey thing after a boot-up / OS hard drive failed on me
Up until today I always worked with 2 drives in computer 1 was the boot drive other held all my work, photos etc
Then I started dual booting winxp "needed" and ubuntu which I like, both of these were on my boot / OS drive that failed (6 weeks old) so I got it replaced this time a SATA drive
Disc 1 is my dual boot drive winXP and Ubuntu 64bit version 10
Disc 2 is my old work drive 
Disc 3 is the new drive which I did install ubuntu on to for testing. disc working

How do I get Ubuntu to see this drive for storage of any work that I do in Ubuntu, might even some day down load some thing,

Should add, that the disk utility in System/admin, confirms the disc is there, or should that be here on this computer

Dave

---

### Post by Dutch70 on 2011-05-06
I'm not sure I understand your question or what you are trying to accomplish.

Does Gparted recognize it? 

If so, just format it to ext3,ext4 or ntfs.

---

### Post by oldfred on 2011-05-06
If it is already partitioned, you may want to add it to fstab to automaticlly mount it on boot.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

I prefer to do it manually, as last time I used one of the gui tools I had to edit it anyway. You do need to understand some of the settings explained in above fstab & permissions links above even with the gui tools.
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)

---

### Post by DaveMcC on 2011-05-06
OK, I want it formated to be the same as Ubuntu
Then when I click on Places, I wish to see it with the other drives displayed

Does that help

Dave

---

### Post by oldfred on 2011-05-06
You need to create & format partition(s) on the drive.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Then you can add the partition to fstab, depending on where you mount it will be where it shows in Nautilus.

---

### Post by BertN45 on 2011-05-06
You have the disk utility installed, so you don not have to install new software. You will have to select the new drive in the left pane of the disk utility.

If it is a new drive, you have to create a partition and format that partition/volume.

Those buttons are readily available in the right pane of the disk utility. If you have done that successfully you will find the Mount Volume Button in the right pane and you can use that to mount your volume. Afterwards you can use your new drive.

If you want the volume to be mounted automatically during the boot, you will have to add a line to the file /etc/fstab. I would google for fstab to find out what to do in your case. Otherwise you will have to click the volume in Places each time to get it mounted. Sorry but it is one of the left-overs of the more geeky days of Linux.

---

### Post by DaveMcC on 2011-05-06
Since I last logged in, I have managed to install and run KDE Partition Manager 1.0.3
It tells me the drive is unallocated and has No Mount Point

Sorry to say I am an old silly ??? and don't know how to either or even next

I need step by step hand holding

Dave

BertN45
I had "or so I thought" the disk formatted when I first ramed it into this boot unit and had Ubuntu 64bit running on it for about 2hrs?

---

### Post by oldfred on 2011-05-06
I have never used kde's partition manager, but it looks similar to others.

[http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/usermanual.html](http://docs.kde.org/development/en/extragear-sysadmin/partitionmanager/usermanual.html)

---

### Post by BertN45 on 2011-05-06
From what you wrote:

     Since I last logged in, I have managed to install and run KDE Partition Manager 1.0.3
     It tells me the drive is unallocated and has No Mount Point

I expect you disk is displayed by the Disk Utility as shown (click on the picture to enlarge it):
[ATTACH]191408[/ATTACH]

If the 6th line is not saying "Master Boot Record" you have to "Format Drive" first and select there "Master Boot Record".
Push "Create Partition" and use the defaults, just change the volume/partition name to one you like. The next choice you have is here:

[ATTACH]191409[/ATTACH]

Format the volume and use the defaults, again change the name if you like. 

After formatting you can mount the volume using the button appearing after the formatting completed. Formatting can take a long time. The disk is ready to use.

---

### Post by DaveMcC on 2011-05-07
Thanks every boby for their help, up and running.  Just hope I can save some stuff on it now..

Dave
:D


:popcorn:

---

