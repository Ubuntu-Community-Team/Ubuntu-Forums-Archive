---
title: "VirtualBox problems with Jaunty host"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by BoundaryNoob on 2009-07-12
Not sure if this should have been posted on the 'Desktop Environments' forum, but I am pretty new so trying here first.

I have successfully installed VirtualBox Version 2.2.4 r47978 onto a Linux host (Ubuntu Jaunty) and am running Windows XP SP3 as a guest with partial success. However I have two problems:

Problem 1.
My virtual disk containing the XP image is on an NTFS formatted drive in a folder created under Windows.  I have no problem reading and writing to this drive using Ubuntu. However if I try to start  Windows as a VB guest as a regular user I get an error that the virtual disk is not accessible. If I then just open the hardware drive containing the Windows image as root I can then start the Windows guest normally.

I would like to be able to use the Windows guest as a regular user. I assume I have a permissions problem.  I have checked that I am a member of the group vbusers and I am.  The permissions shown for the folder containing the image are shown as read and write for owner, group and others.  Root is shown as the owner.  Within Windows I have also enabled sharing of the folder with all users of the computer and my home network. 

Can anyone see what I am missing?

Problem 2.
I originally installed VirtualBox under Linux kernel 2.6.28.11.  When this was updated to 2.6.28.13, I started getting an error: 

'Kernel driver not installed (rc=-1908)'. The VB Linux kernel driver (Vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv.....

Following the instructions on the error message, I installed the DKMS package and tried re-setting-up the kernel module by executing  /etc/init.d/vboxdrv setup as root.  It still doesn't work.

Any suggestions?

---

### Post by Delever on 2009-07-12
> **BoundaryNoob said:**
> Not sure if this should have been posted on the 'Desktop Environments' forum, but I am pretty new so trying here first.

I have successfully installed VirtualBox Version 2.2.4 r47978 onto a Linux host (Ubuntu Jaunty) and am running Windows XP SP3 as a guest with partial success. However I have two problems:

Problem 1.
My virtual disk containing the XP image is on an NTFS formatted drive in a folder created under Windows.  I have no problem reading and writing to this drive using Ubuntu. However if I try to start  Windows as a VB guest as a regular user I get an error that the virtual disk is not accessible. If I then just open the hardware drive containing the Windows image as root I can then start the Windows guest normally.

I would like to be able to use the Windows guest as a regular user. I assume I have a permissions problem.  I have checked that I am a member of the group vbusers and I am.  The permissions shown for the folder containing the image are shown as read and write for owner, group and others.  Root is shown as the owner.  Within Windows I have also enabled sharing of the folder with all users of the computer and my home network. 

Can anyone see what I am missing?

Problem 2.
I originally installed VirtualBox under Linux kernel 2.6.28.11.  When this was updated to 2.6.28.13, I started getting an error: 

'Kernel driver not installed (rc=-1908)'. The VB Linux kernel driver (Vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv.....

Following the instructions on the error message, I installed the DKMS package and tried re-setting-up the kernel module by executing  /etc/init.d/vboxdrv setup as root.  It still doesn't work.

Any suggestions?

Uninstall vbox (it won't delete your .VirtualBox directory), and try latest version 3.0.0.

---

### Post by BoundaryNoob on 2009-07-13
> Uninstall vbox (it won't delete your .VirtualBox directory), and try latest version 3.0.0. 

Thanks for your help Delever!  That's sorted out Problem 2 - I can start VB using the latest ubuntu kernel.

Do you have any ideas about my permissions problem?  I still can't start Windows guest without working as root.

---

### Post by carml on 2009-07-13
Can you post a screenshot of the section with vboxusers?

---

### Post by lkraemer on 2009-07-13
BoundaryNoob,
Did you install the Ubuntu version (32 bit or 64 bit) PUEL version from
[www.VirtualBox.org](www.VirtualBox.org) or the ANY VERSION Script from their site?
There are some differences in what subdirectories are created, and
where files are stored according to the VirtualBox Forum.

If you are using Ubuntu as the HOST, and XP as the GUEST, why is the
VDI placed in a WINDOWS folder?
 
When you installed VirtualBox in Ubuntu it should have created a hidden folder
in your /home/USER folder (where USER is your loginname) named
.VirtualBox
You can use CNTL H to make those folders visible from your HOME folder
or toggle it off again.

Under the .VirtualBox folder you should have two folders.
Machines & VDI

The VDI folder should contain your Windows.vdi file

OR for later versions the folders will be:

HardDisks & Machines 

The HardDisks folder should contain your Windows.vdi file

Is your VDI located there?  Your post states it is placed at a different
location.  When you installed VirtualBox in Ubuntu and then Windows
in VirtualBox, VirtualBox should have placed the VDI file in the proper place.
You may want to try copying the file to the proper location in Ubuntu.

You also will need to make sure the Guest Additions CD installed.

To execute the Windows.vdi, you open Virtualbox from the menu,
APPLICATIONS -> SYSTEM TOOLS -> VIRTUALBOX
attach the vdi to the master or slave channel you want, along with 
selecting the *.vdi you want, and then left click on start.
Windows should start to boot, then come up running.

Is this the procedure you are using?
 

Also make sure you do:
```

sudo adduser $USER vboxusers

```

lkraemer

---

### Post by BoundaryNoob on 2009-07-13
> Can you post a screenshot of the section with vboxusers? 

I am attaching the screenshot carml.

> Did you install the Ubuntu version (32 bit or 64 bit) PUEL version from [www.VirtualBox.org](www.VirtualBox.org) or the ANY VERSION Script from their site?
There are some differences in what subdirectories are created, and
where files are stored according to the VirtualBox Forum.

lkramer, I downloaded the i386 version for Jaunty at the top of the list on this page:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I have a 32 bit machine.  Is this OK?

> If you are using Ubuntu as the HOST, and XP as the GUEST, why is the VDI placed in a WINDOWS folder?

Originally all my physical drives were created using Windows, then I added a Ubuntu partition and have been operating with dual boot.  The reason I put the VM on a Windows drive was that was where I had most space!

> Under the .VirtualBox folder you should have two folders.
Machines & VDI
The VDI folder should contain your Windows.vdi file
OR for later versions the folders will be:
HardDisks & Machines
The HardDisks folder should contain your Windows.vdi file
Is your VDI located there? Your post states it is placed at a different
location. When you installed Windows, VirtualBox should have placed the
VDI file in the proper place. You may want to try copying the file to the
proper location.

OK lkramer - I think this could be the problem!! I have the .VirtualBox folder in my HOME folder, containing the Machines folder but not VDI or HardDisks.  As I have the latest version of VB it sounds as if I should have a HardDisks folder.  I have tried creating a HardDisks and copying the .vdi file to it but have run out of space on my Ubuntu partition!

Looks as if the way out of this will be to do some repartitioning.  I'll have a go at this tomorrow.

> You also will need to make sure the Guest Additions CD installed.

Yes I have them installed.

> To execute the Windows.vdi, you open Virtualbox from the menu,
APPLICATIONS -> SYSTEM TOOLS -> VIRTUALBOX
attach the vdi to the master or slave channel you want, along with
selecting the *.vdi you want, and then left click on start.
Windows should start to boot, then come up running.
Is this the procedure you are using?

Yes I think so. When the VirtualBox window comes up I am just selecting the XP VM and hitting 'start'. Up to now I have typically got the error message about the virtual drive not being accessible until I have navigated to the .vdi file as root, after which 'start' works and Windows comes up running.

I really appreciate the help I'm getting on this - thanks!

---

### Post by lkraemer on 2009-07-13
Well, everything appears to be what I have, except for your VDI
file being located on the Windows Partition.

I wonder what your file permissions are for the windows VDI folder and the
actual vdi file?  I have included two png's.  One of the permissions
of my .VirtualBox folder (same permissions on folders HardDisks & Machine
as well as the actual vdi files) and the second is of my vdi files.
Notice the path to the vdi in the lower portion of the png.

If you change your permissions so they are the same maybe it will work,
but I wouldn't want to be reading and writing to the Windows partition
for fear of something going wrong and having a blown XP Install.
I'd rather see you have a fresh VirtualBox install, with the proper
folders built by VirtualBox, then just copy your vdi files from the
windows partition to the Ubuntu Partition and set up a new Expanding
Hard Drive referencing your copied vdi file.  I have done this and it
all works fine.  In fact the xpsp3.vdi file displayed here was copied
from a DVD-DL and it works just fine from a 2.06 VirtualBox install
on the lastest 3.0.2 revision.

And, when you need to expand your VDI because it is maxed out after the
Windows install, and by installing 3-4 software packages ref Post #5 here.
I've used it and it works.

[http://ubuntuforums.org/showthread.php?t=723219](http://ubuntuforums.org/showthread.php?t=723219)

Another thing you could try, is to rename the .VirtualBox folder to
.ZirtualBox, then re-make an XP VDI by creating a NEW, and
changing all the settings as your hardware requires.  Then copy any
*.vdi files from the .Zirtual/HardDisks folder to .VirtualBox/HardDisks,
then delete the .ZirtualBox folder.  That should get all the proper folders
generated for VirtualBox running on Ubuntu and allow your GUEST OS
(XP) to run in VirtualBox.

I just hope that at this point you aren't trying to use a raw host
hard disk as a guest as referenced in the manual section 9.10 as
it most likely could be a disaster for the XP partition.

lkraemer

---

### Post by BoundaryNoob on 2009-07-14
> I wonder what your file permissions are for the windows VDI folder and the actual vdi file?

Thanks lkraemer.  My file permissions are the same as yours for the .virtualbox folder, but root is the owner of the VDI file out there in Windows-land. The immediate problem is that it won't let me change the permissions.

I'm attaching a png of my virtual media manager panel - the path is to the NTFS Images-Music partition (I really should try to choose shorter file/folder names!) The weird thing here is that my VDI file is showing as really small in the media manager, although its actual size is 4.2GB - it works fine once launched anyway.

> If you change your permissions so they are the same maybe it will work,but I wouldn't want to be reading and writing to the Windows partition for fear of something going wrong and having a blown XP Install.  I'd rather see you have a fresh VirtualBox install, with the proper folders built by VirtualBox, then just copy your vdi files from the windows partition to the Ubuntu Partition and set up a new Expanding Hard Drive referencing your copied vdi file. 

I've got the Windows OS on a separate partition from the one I've got the VDI file on (which has only got data on it).  But I think you're right - it would be much cleaner to keep things separate and put the VDI on the ubuntu partition.  I'm working on expanding the ubuntu partition now.  Looks like it'll have to be tomorrow though.

> And, when you need to expand your VDI because it is maxed out after the Windows install, and by installing 3-4 software packages ref Post #5 here. I've used it and it works.
[http://ubuntuforums.org/showthread.php?t=723219](http://ubuntuforums.org/showthread.php?t=723219)

This could be invaluable when I'm a little further down the line....

Thanks again for your help.  I'll be on the case again tomorrow!

Andrew

---

### Post by carml on 2009-07-15
I checked my vboxusers and it shows the number 124 instead of 130 as your do,I don't know if this can help. :confused:

---

### Post by BoundaryNoob on 2009-07-15
Hi lkraemer

OK I'm making progress (I think).

I've expanded the ubuntu partition and successfully copied the vdi file from the windows partition to the HardDisks folder in .Virtualbox.

There is some unexpected good news.  For reasons that I can't work out, the vdi file on the windows partition is now being indirectly attached using a differencing hard-disk and is enabling me to start windows completely normally without having to work as root! (see attached screenshot 1).

I suppose at this point I should say 'if it ain't broke don't fix it' and just get on with my life, but now I'd really like to operate from the ubuntu partition as you suggest.  The bad news is that I have not been able to attach the newly copied vdi file in the HardDisks folder.

I've tried creating a new vdi (called Reborn_XP_SP3) and then transferring my existing windows vdi and renaming it Reborn_XP_SP3, but it insists on referencing the original file on the windows drive indirectly and not reading the renamed local file.  See attached screenshot 2.

I'm probably missing something obvious - can you help?

---

### Post by BoundaryNoob on 2009-07-15
Hi carml

> I checked my vboxusers and it shows the number 124 instead of 130 as your do,I don't know if this can help. 

I assume the Group ID is arbitrary depending on how many groups you have already defined when you add the new one.  My number 124 is called dirmngr.

I'll come back to this if other possible solutions fail!

---

### Post by carml on 2009-07-15
You can manage your vdi from within Virtualbox and yes when you for example delete a disk or a iso associated to a disk you'll be prompted by a warning.
From the menu File under Virtualbox you access to the Virtual Support Handler,from there you can add/remove your virtual disk(s).
If you need more help just ask and someone will answer.

---

### Post by lkraemer on 2009-07-15
Well, why don't you try to release that VDI image, then remove
it (just DON'T DELETE it in the next setp) by clicking on the folder.
Then use the add feature to add the fresh copy that is located in the
HardDrives folder.  (You can always go back to the previous one
as long as you DO NOT DELETE it.)

When you REMOVE it it removes the VDI image associated with your
Virtual Disk Image.

That should work.

So, RELEASE, REMOVE, ADD (new Image), Execute

lkraemer

---

### Post by BoundaryNoob on 2009-07-16
OK Guys - I think it's sorted!

There was one final hurdle that I'll report for the record.

> So, RELEASE, REMOVE, ADD (new Image), Execute

When I tried to remove the original vdi on the Windows partition and add the local one, VirtualBox would not do it because it still had reference to the original one in the registry held in the /home/al/.VirtualBox/VirtualBox.xml file.

I removed the lines in the hard disk section of this file (referring to the old vdi and associated snapshots), saved and was then able to add the new vdi in the usual way.  Windows is now running perfectly.

Thanks again for all your help!

Andrew

---

### Post by lkraemer on 2009-07-16
Andrew,
You should have been able to RELEASE, REMOVE, etc from this menu
selection shown in the png.  Just be sure of what you are deleting,
as once deleted, the vdi is gone from the .VirtulBox/HardDrive folder.

lkraemer

---

### Post by BoundaryNoob on 2009-07-17
Thanks Larry

Yes this was the menu I used to remove the reference to the unwanted disk on the Windows partition and add the new one in my/home/al/.VirtualBox/HardDisks folder.

The first step had to be done as root - you may remember that root was owner of the Windows tbi.  At the second step I was told that I could not add the new disk because the old one was still registered in the /home/al/.VirtualBox/Machines/VirtualBox.xml file.  When I removed the lines referring to HardDisks in the hml file, I was then able to add the new one without any hitches using the method you described.  VirtualBox had automatically modified the xml file with the correct hard disk. 

I'm pretty confident that all is now as it should be.

Andrew

---

