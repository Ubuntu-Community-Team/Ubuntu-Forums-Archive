---
title: "Move /home directory to another hard drive"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by wiganbotch on 2010-12-02
Hi there,  Complete Linux newbie, so please be kind....My computer has three hard drives.  I have performed a clean install of Ubuntu 10.10.  I selected the default options and the install went smoothly.  The only issue I encountered was a missing video mode but I was able to fix this using guidance on these forums.  The filesystem has been installed on the first of my hard drives **(sda)**.  This has a single partition **(sda1)**.  These are my current settings.

[B]80 Gb    sda     sda1   Ext 4    /
250Gb   sdb     sdb1   Ext4     /media/sdb1 *
165Gb   sdc     sdc1    Ext4     /media/sdc1*

[/B]* I created these partitions using the disk utility (Ext4 filesystem) and mounted them to the deault location (/media)
I would like to move the **/home **directory to the 250Gb drive.

_Failed Attempts_

I have tried to move the **/home** directory using the GUI from **sda1** to **sda2** but this did not work.  The files moved across but the home location for the users did not actually change.

I also changed the location of the **/home** directory for all users in the advanced user accounts settings to **/media/sdb1/home/*name***.  But after a reboot the home folder still pointed to **sda1** 

I have searched the forums and there are walkthroughs for moving the **/home** directory to another partition on the same drive, but I have been unable to find one specifically relating to moving the **/home** directory to another drive.  

_Help!_

Any advice would be appreciated.  Below are a some of questions that I hope someone can help me with:

* Where do I need to mount** sdb1?**  The default location seems to be **/media/sdb1**.  Can I mount **sdb1** directly to the home directory (**mnt /dev/sdb1 /home**) or am i being stupid?

* What file system should I use for **sdb1**?  The drive will be used mainly to store my MP3 collection.  I want to share folders on the drive with another computer (XP) on my network

* Do I need to alter the fstab?  I downloaded the pySDM program.....had a play about  without doing enough research and now my system won't boot!  Never mind I'll do another clean install and try again.

Thanks in advance.

Paul

---

### Post by theDaveTheRave on 2010-12-02
Paul,

if you are about to perform a clean install, you can simply use the 'advanced' options and tell the system to put the home directory on the 250GB HDD.

If on the other hand you want to perform a clean 'default' install feel free.

You will then need to manually edit the /etc/fstab file to tell it where to find the '/home '  directory, and where to mount it too. As you say mnt /dev/sdb1 /home should do the trick, but you'll require some extra option in fstab file.

check out this [thread]("http://ubuntuforums.org/showthread.php?t=283131") by bodhi.zazen (if you haven't already) it will give you the extra info you require.

David

---

### Post by bioterror on 2010-12-02
Copy your home to that new drive.
After that edit /etc/fstab and add following

```
/dev/sdb1 /home ext4 defaults 0 2
```

You could boot with LiveCD and "move" that home to new a drive also, that's what I would do. Or you could use recovery mode's root login.

But you cant be logged in with your normal user account which you're moving becouse the files are being used.

---

### Post by bioterror on 2010-12-02
PS. I would suggest to use UUID instead of /dev/sdXX.

---

### Post by oldfred on 2010-12-02
If you just want to have your music look like it is in your /home, all you have to do is link the folder into /home. You still need to create a mount point & mount it with fstab to have it permanently mounted. I do this for about 12 folders in my /data partition.
Similar thread:
[http://ubuntuforums.org/showthread.php?t=1635717](http://ubuntuforums.org/showthread.php?t=1635717)

Or if it is just one folder/directory you can just directly mount it with fstab into /home. I used to do this for my /shared NTFS partition.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)
Storage Device Manager - Worry-Free Fstab Configuration
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

If you want to move /home:
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

