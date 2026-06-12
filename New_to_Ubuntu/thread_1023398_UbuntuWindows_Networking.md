---
title: "Ubuntu/Windows Networking"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by jbuczek on 2008-12-27
Be gentle.  I was in the business for 35 years but I've been out for 10 now and I'm old, tired and getting more stupid by the moment.

I've set up a very low power, fanless, VSFF (very small form factor) box to be a 24/7 file/printer server for our 3 WinXP boxes.  As I master Ubuntu, I'll try to wean us away from Win.  I have the desktop version of Ubuntu 8.10 installed on this "server".

So... the boot drive is a 2 gb CF card which the hardware apparently disguises as a HDD because Ubuntu install immediately recognized it as that.  Then there is a 300 GB USB drive partitioned into a 100GB ext3 drive and a 200GB Fat32 drive.  The ext3 drive has /usr, /tmp, /homes and one or two others on it.

The purpose of the Fat32 drive is to share files (music, pictures, backup space, etc) with both Ubuntu and WinXP boxes.  I installed and set up minimalist SAMBA.  Everything works great as long as the user is "john".  That's me.  Administrator on both sides.  Other users can see the server and access folders created by Ubuntu (/homes for example) but if they try to open any folder I've created they get the message:

     "Not Accessable.  You might not have permission... etc"

Permissions are: "drwx______", owner "john, group "root" and are the same for the accessible folders as well as the unaccessible. I cannot change those permissions with chmod or with the File Manager.  I cannot change ownership or group either.  I tried "sudo chown ....." and so forth but that doesn't work either.

Research says Ubuntu is happy with vfat so that's probably not it.

I've created identical Win, Ubuntu and SAMBA ID's and passwords for all users.  We are all members of the same Win workgroup and Linux group which have the same name.

I note that there is no fstab entry for this partition but........ it's working, at least partly so.

BTW.... my SAMBA config file does not create a HOMES share.  What's making that public?

I could really use a clue.

---

### Post by blueridgedog on 2008-12-28
I too have been out of the field a bit, but I can lend a small hand.

Fist, your fat32 disk can't have permissions of files or directories changed.  The file type don't recognize such things and the entire device is mounted under one user/group.

As a USB drive, it will have no entry in fstab.  Some new process automounts them (I think it is part of hald).

So you have two problems at the start, you can assign permissions to the 200GB and it is mounted automatically (under /media???).

I suggest you manually mount the fat32 partition on the USB drive so you can open up the permissions a bit.

To find out more, paste back the output of 

```
fdisk -lu
```
 
Assuming you find out your USB drive is called /dev/sdc and the fat32 partition is 2 (example only mind you), after unmounting it, we can create an entry in fstab that will mount it more "wide open" such as:


```
/dev/sdc2 /SharedFiles vfat rw,noatime,nosuid,nodev,noexec,nouser,async,iocharset=utf8,umask=0 0 0
```

Note "/SharedFiles" is your mount point in your file system and I made it up just like I made up /dev/sdc2 as an example.

---

### Post by hyper_ch on 2008-12-29
if you use samba to share among the network then you can also use ext3 as underlaying system - actually I'd recommend that.

---

### Post by jbuczek on 2009-01-04
Thank you, gentlemen.  I came to the conclusion that my problem had something to do with the "mount" process and was reading up trying to figure it out myself.  I'll try your suggestion.

As to changing the drive to ext3, not in the cards ... at this time anyway.  I'm retired.  I live in the Philippines. The power here is hyper dirty resulting in frequent computer breakdown in spite of a 1500 watt voltage regulator AND a UPS.  The linux box is intended to be a server for the other computers to backup and to share photo's, music and documents.  I ALSO want it to be a backup computer in case my main Windows box goes down.  So I will put mail files (Thunderbird), browser files (Firefox), Treepad data files (a free form textbase which contains everything I know or want to recall) and my documents on this drive and either sync them or back them up both ways.  The idea is that the data will be accessable from both of my computers when they are working.  If the Ubuntu box goes down I want to be able to unplug the USB drive, plug it into the Win box and be up and running with my data.  Thus.... FAT32.

If you have any suggestions for accomplishing the same with ext3 or whatever I'd be glad to hear.

When I get more at home with Ubuntu, I'll learn how to set up my Win box to run Ubuntu with a WinXP VM for my CAD program and a few others which aren't available in linux yet.  They I can abandon fat32.

I can't wean my wife and the other folks around here away from windows because of the games they are addicted to and their educational stuff.

Regards

---

### Post by hyper_ch on 2009-01-05
windows can access ext3

---

### Post by jonandrews on 2009-01-05
Hi. Firstly, the file systems used on the PC's is completely irrelevant to networking between them. All writing to a disk is controlled only by the operating system of the pc in which the disk is installed. 

To get an overview of the configuration you need, have a look at my Windows / Unbuntu networking guides at

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

