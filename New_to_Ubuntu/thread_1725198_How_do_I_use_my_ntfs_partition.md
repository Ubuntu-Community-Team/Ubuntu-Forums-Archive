---
title: "How do I use my ntfs partition"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by maembe on 2011-04-09
I mounted an ntfs partition (the C drive in Windows 7), but I don't really know what to do with it.  It's there, and I can open it in kubuntu, but when I log into Windows and try to add anything says that I'm not allowed to save any files in it.  Does it only go one way?

How do people normally use their ntfs partition?  Ideally, for me, I would like a way to have music and document files that I can access on both windows and kubuntu.  Is this the correct use?  What else do I need to know/do?  Can I rename it?  Is it safe to mess with stuff like that?

More questions to follow I'm sure.
Thanks for your help.

---

### Post by oldfred on 2011-04-09
Much better to create another NTFS partition (D: in windows) and set that to read/write in Kubuntu. 

Writing into another system partition is prone to causing problems. Linux lets you see all the normally hidden files in windows and lets you corrupt system. If you hibernate in windows writing anything will corrupt it as the hiberfile is looking for info in the wrong place.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Shared NTFS partition - You can also use links
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by SeijiSensei on 2011-04-09
> **maembe said:**
> I mounted an ntfs partition (the C drive in Windows 7), but I don't really know what to do with it.  It's there, and I can open it in kubuntu, but when I log into Windows and try to add anything says that I'm not allowed to save any files in it.  Does it only go one way?

Windows has no native support for filesystems other than NTFS and FAT32.  To access your ext3/ext4 Linux partitions from Windows requires a special [driver]("http://www.ext2fsd.com/").

> How do people normally use their ntfs partition?  Ideally, for me, I would like a way to have music and document files that I can access on both windows and kubuntu.  Is this the correct use?

Yes, that's one common use.  You might be better off repartitioning the hard drive to create a separate partition for those files.  Writing into the Windows OS partition itself can sometimes cause problems.  (I see oldfred made these same points while I was writing this.) Another common option is using an NTFS-formatted external USB drive.

> Can I rename it?

The "name" assigned to the partition is nothing other than the name of a directory in the Linux filesystem tree into which the partition is "mounted."  Suppose you told the Ubuntu installer to mount your Windows filesystem at /windows.  You could change that to any other name, but it would require making some changes to the system configuration files.  Here, for instance, I move the partition from /windows to /media/harry:

```

sudo umount /windows
sudo mkdir /media/harry
sudo cd /etc
sudo cp fstab fstab.old
sudo sed 's%/windows%/media/harry%g' < /etc/fstab.old > /etc/fstab
sudo mount /media/harry

```

I used the simple command-line editor sed to replace "/windows" with "/media/harry".  You could do it in a full-screen editor, too, by typing "sudo nano /etc/fstab".

Now why you'd want to do this is a different question, but I presume you have your reasons.

> Is it safe to mess with stuff like that?

Only if you know what you're doing first.  If you've not been using Linux for very long, and don't really know your way around a terminal prompt, I'd say leave things be for now.

---

### Post by maembe on 2011-04-16
How do I resize my current partitions?  I can't in Windows 7 and I can't unmount a partition I'm using so I don't really understand how to do it.

---

### Post by K_45 on 2011-04-16
In Windows 7, click start, right click on computer, select Manage. Yes to UAC, then select Disk Management. Then right click the drive and shrink. Before you do shrink, note the space that can be shrunk. If it isn't enough, post back, if it is, shrink, then boot into Ubuntu. Then post here how much you've shrunk and we can start using Gparted to use that partition.

---

### Post by maembe on 2011-04-16
> **K_45 said:**
> In Windows 7, click start, right click on computer, select Manage. Yes to UAC, then select Disk Management. Then right click the drive and shrink. Before you do shrink, note the space that can be shrunk. If it isn't enough, post back, if it is, shrink, then boot into Ubuntu. Then post here how much you've shrunk and we can start using Gparted to use that partition.

Thats the problem, I already shrunk it to install ubuntu, so I can only shrink it 200MBs.

---

### Post by K_45 on 2011-04-16
Boot up Gparted as a LiveCD and shrink with that instead.

---

### Post by maembe on 2011-04-17
Okay, so I shrunk my Windows and my Ubuntu partitions.  So right now I have:

/dev/sda1  ntfs (the Windows sytem one)  1.46GiB
/dev/sda2  ntfs (my Windows partition)
unallocated  190.35 GB
/dev/sda3  extended  221.21 GiB  (this one has three inside it, I put a dash in front of them)
     -  /dev/sda5  ext4 (Ubuntu)  13.67 GiB
     -  unallocated  198.22 GiB
-  /dev/sda6  (linux swap)  9.31 GiB
/dev/sda4  ntfs  /media/HDDrecovery  11.72 GiB

So shrinking two partitions gave me two separate unallocated partitions.  Also, I have 4 primary partitions, so I'm not sure what I should do from here.

---

### Post by Jerry N on 2011-04-17
> **K_45 said:**
> Boot up Gparted as a LiveCD and shrink with that instead.

DO NOT under any circumstances use gparted to shrink your Windows 7 NTFS partition.  Such an action can damage the partition, possibly irreversibly.

Jerry

---

### Post by maembe on 2011-04-17
> **Jerry N said:**
> DO NOT under any circumstances use gparted to shrink your Windows 7 NTFS partition.  Such an action can damage the partition, possibly irreversibly.

Jerry

Well crap.

---

### Post by K_45 on 2011-04-17
> **Jerry N said:**
> DO NOT under any circumstances use gparted to shrink your Windows 7 NTFS partition.  Such an action can damage the partition, possibly irreversibly.

Jerry

 That can happen with any partition, with the emphasis on *can.*

---

### Post by oldfred on 2011-04-17
We recommend you use windows to resize as we do not know for sure what version of gparted you are using. Older version of gparted would work also but often moved the start of the windows partition from sector 2048 to sector 63. Win7 works from sector 63 but then required chkdsk and fixboot at the minimum to repair. Now gparted defaults to 2048 for all first partitions, so it does not move window and cause problems. But any change to windows will want windows to run chkdsk on a reboot. 

Best to reboot windows after resizing to get it to run chkdsk and confirm there are no issues. Do this before installing Ubuntu.

---

### Post by maembe on 2011-04-17
Well, Windows won't boot up anymore.  Any suggestions?

---

### Post by K_45 on 2011-04-17
This will fix it:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by maembe on 2011-04-17
Fixed that.  So now what do I do to set up my ntfs partition?

EDIT:  Here is where I'm at now:

Okay, so I shrunk my Windows and my Ubuntu partitions.  So right now I have:

/dev/sda1  ntfs (the Windows sytem one)  1.46GiB
/dev/sda2  ntfs (my Windows partition)
unallocated  190.35 GB
/dev/sda3  extended  221.21 GiB  (this one has three inside it, I put a dash in front of them)
     -  /dev/sda5  ext4 (Ubuntu)  13.67 GiB
     -  unallocated  198.22 GiB
-  /dev/sda6  (linux swap)  9.31 GiB
/dev/sda4  ntfs  /media/HDDrecovery  11.72 GiB

So shrinking two partitions gave me two separate unallocated partitions.   Also, I have 4 primary partitions, so I'm not sure what I should do  from here.

---

### Post by oldfred on 2011-04-17
Where do you want the space?

I would expand extended partition to cover all the unallocated. Then you can create a NTFS shared partition in the first unallocated and create /home in the second unallocated. Then use manual install to select which partition is which (where to mount) & what format.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by maembe on 2011-04-17
> **oldfred said:**
> Where do you want the space?

I would expand extended partition to cover all the unallocated. Then you can create a NTFS shared partition in the first unallocated and create /home in the second unallocated. Then use manual install to select which partition is which (where to mount) & what format.



What is the /home partition for?  Don't I just need an ntfs?  Also, what do you mean by manual install?  Are you talking about installing Ubuntu?  Cause it's already installed in the extended partition.

---

### Post by oklokl on 2011-04-17
sudo apt-get install ntfs-3g
sudo apt-get install mountmanager

[COLOR=#555555][FONT=Verdana]sudo chown -hR [COLOR=RoyalBlue]*IDuerhome*[/COLOR] /media/windows7[/FONT][/COLOR]

---

### Post by oldfred on 2011-04-18
If you have /home in the extended partition you posted as unallocated then that is fine.

Just expand the extended partition left to include the unallocated so you can create a new logical partition. Format it to NTFS.

Best to permanently mount. You already should have the NTFS drivers. I think oklokl's suggestion of mountmanger works. I have used some of the auto mount and had to reset things manually in fstab.

Even if you use some gui tools to mount it helps to know what the settings are as most do not explain them well:
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

A couple of other gui tools. You really only need one. And may have to do some manual edits.

Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)
Storage Device Manager - Worry-Free Fstab Configuration
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by maembe on 2011-04-18
> **oldfred said:**
> Where do you want the space?

I would expand extended partition to cover all the unallocated. Then you can create a NTFS shared partition in the first unallocated and create /home in the second unallocated. Then use manual install to select which partition is which (where to mount) & what format.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

 I expanded the extended partition, but it won't let me combine the unallocated spaces, so I have 2 unallocated spaces that each have over 200GB.

---

### Post by oldfred on 2011-04-19
If you have partitions between the unallocated, you cannot combine them.

Gparted will let you move partitions, but it is a bit more risky as every bit of data is copied & verified. If you have a power failure it will cause huge problems and depending on how much data you have, it can take a long time. You may have to reinstall grub's boot loader. Be sure you have good backups.

---

### Post by maembe on 2011-04-19
All right!  I got it all set up.  Thanks for your help everyone.   One last question before I mark this as solved.  How do I unmount my windows partitions in Ubuntu.  I don't want them to show up at all.  Is that possible?

---

### Post by K_45 on 2011-04-19
Show paritions with

```
mount
```

unmount with 

```
sudo umount dev sdX
``` replace X with info from mount.

More info here:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by oldfred on 2011-04-19
I mount my partitions in /mnt/shared creating shared as the mount point. Then you do not see them unless you search in /mnt. But I link folders into /home to make the folders I want to use available. And I set the path in Firefox & Thunderbird profiles to /mnt/shared/.... as I have them fairly deep in my file structure.

---

### Post by rosencrantz on 2011-04-19
> **maembe said:**
> All right!  I got it all set up.  Thanks for your help everyone.   One last question before I mark this as solved.  How do I unmount my windows partitions in Ubuntu.  I don't want them to show up at all.  Is that possible?

If they are not in /etc/fstab, they are not permanently mounted at boot. They do however show up in Places and Device Manager as mountable, so you can probably mount them read/write with a mouse click, which is indeed not the safest thing to do for a Windows system partition.
How about mounting them permanently in fstab, but read only?
They won't show up in either Places or Device Manager, and you can't accidentally modify anything.

---

### Post by maembe on 2011-04-20
So how do I do that?

---

### Post by oldfred on 2011-04-20
See post #19.

---

### Post by maembe on 2011-04-20
Well, I almost got this figured out thanks to PySDM, but for some reason, my SDA1, the windows System partition, doesn't show up so I can't do anything to it.

---

### Post by oldfred on 2011-04-20
The windows system partition is not anything you want to mount anyway. It is a hidden partition in windows, not sure about Ubuntu. It is only for booting and repair of windows.

---

### Post by maembe on 2011-04-21
> **oldfred said:**
> The windows system partition is not anything you want to mount anyway. It is a hidden partition in windows, not sure about Ubuntu. It is only for booting and repair of windows.

That's the problem, I don't want to mount it.  I meant that it doesn't show up in PySDM, so it's just stuck on my desktop and is automatically mounted at startup and I can't do anything about it.  Sorry for the confusion, I should have been more clear.

---

