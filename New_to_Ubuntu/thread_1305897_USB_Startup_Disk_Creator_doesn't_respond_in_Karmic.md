---
title: "USB Startup Disk Creator doesn't respond in Karmic"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by shof2k on 2009-10-30
Has anyone else had any problems using the USB Startup Disk Creator (usb-creator-gtk)? I can start it, but it wants to format my empty USB drive.  Clicking format has no response. There is no log file or terminal output. 

I've seen [bug 457737]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/457737") but there is no advice there.  

How did this get passed testing?

**Edit**
Workaround found in GTP-Hanks post. Basically, create a FAT32 partition first then select the partition instead of the disk.

---

### Post by cybil on 2009-10-30
Yes, I have the same issue.  I wanted to create an img of the netbook remix, which was not provided in both iso and img this time around, and I could also not format the usb key.  I can select the iso, but can't create since it says the usb needs to be formatted.  Manually formatting does not help.

---

### Post by ubuntu1 on 2009-10-30
Exactly the same issue here.

---

### Post by GTP-Hank on 2009-10-30
I've had the same experience, in upgrade to 9.10 from 9.4.  Reinstalling usb-creator and dependent packages is no help for me. Hopefully this'll get fixed soon.

I was successful using this work-around method:

Open gparted 
[LIST]
[*]erase usb disk.
[*] create a single fat32 partition
[*]note name of partition created
[/LIST]
Open USB startup disk creator

[LIST]
[*] selecting the usb partition just created
[*]ignore flag on hard disk
[*]do NOT hit the "format" button
[*]hit the "create" button
[/LIST]
Gparted may be installed using the following command:
> sudo apt-get install gpartedGparted then shows up under System-->Administration in the menus.

---

### Post by liddler on 2009-10-31
GTP-Hank's method worked - but only after I had removed a couple of CDs I had in CD drives.
It defaulted to my first cd drive and said image was too large and the Make Startup Disk button was greyed out.  Removing the CDs then starting the usb disk creater then worked following GTP-Hank's method

---

### Post by shof2k on 2009-10-31
Confirmed that GTP-Hanks workaround works. Looks like the program is showing the root device (in my case /dev/sdb), when it wants for a FAT32 partition (/dev/sdb1).


I'll put this on the bug and update my original post.

Thanks Folks

---

### Post by CedarSeagull on 2009-11-15
GTP-Hank's method didn't work for me; I think becuase I don't have a working cd-rom drive (which is why I'm doing a usb in the first place).  I've tried putting ext2, ext3 and now fat32 partitions on the drive.  Each time after selecting the .iso file I'd like to use, the "Make Startup Disk" button is greyed out.  I'm really not sure what to do.  Any suggestions?

---

### Post by jebbench on 2009-11-19
It seems the Start Up Disk Creator will work if the drive is unmounted, I've not done any testing but it worked for me when I unmounted the drive.

When I say worked I mean the Format button responded by freezing the application for about 10 seconds, then it sat at flushing the file system 101% complete for 5 minutes.

It's a pretty poor piece of software and should probably be removed form the default install until it's fixed.

---

### Post by kwasibengt on 2009-11-26
CedarSeagull

if you created your FAT32 partition using fdisk instead of gparted you have to format it with the command mkfs.vfat /dev/sdX1 <-- X stands for your device

and in usb-creator-gtk select the same partition and not the device itself.
it worked for me.

if you have an cdrom-drive isnt an issue if you use a .iso from an ubuntu-cd archive as source.

/Richard

---

### Post by cybil on 2009-11-26
I will have to try it.  Thanks!

---

### Post by dkeats on 2009-11-29
I have this problem too. Tried installing Gparted but when I run it I get error, unable to copy the user's Xauthorisation file. Other applications work fine with gksu, so stuck on this. Anyone know if there are any other tools that can replace this  Start Up Disk Creator application? I am only doing this because Update manager seems not to notice the upgrade available on my Dell netbook, which is another issue.

---

### Post by Greenwidth on 2009-11-29
> **dkeats said:**
> Anyone know if there are any other tools that can replace this  Start Up Disk Creator application?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Works for me, though I think I remember seeing some people having trouble. Worth a try.

---

### Post by amishphysicist on 2009-11-30
tried that. get a generic "boot error" message when trying to run it. bleh. sucks. just want to be able to install without burning a CD.

---

### Post by efflandt on 2009-11-30
You have to watch that you format the partition not the drive (for example if the USB is sdb, format and install on sdb1).  If you mess up, use gparted to remove the partition and if necessary recreate msdos partition table (which does not make any partitions, just the table to keep track of them) and then create FAT16 partition for 2 GB or less or FAT32 for larger USB.  I made the mistake of formatting the device instead of partition a number of times.

When you set the slider for persistent data, so not move it to the max.  Make sure it is at least one click down from maximum.  Maybe it estimates file sizes and does not account for files that do not end on full blocks.  Whatever the reason, it seems to hang if you select maximum persistent file size.

---

### Post by stevepowell99 on 2009-12-31
confirming Hank's method works for me.

---

### Post by jpowers1 on 2010-02-02
I'm running 10.04 beta. My startup disk creator would say there wan't space on the drive once i hit format. I unmounted the drive, then hit safely remove...seems to be running now

---

### Post by KcLKcL on 2010-03-08
> **GTP-Hank said:**
> I've had the same experience, in upgrade to 9.10 from 9.4.  Reinstalling usb-creator and dependent packages is no help for me. Hopefully this'll get fixed soon.

I was successful using this work-around method:

Open gparted 
[LIST]
[*]erase usb disk.
[*] create a single fat32 partition
[*]note name of partition created
[/LIST]
Open USB startup disk creator

[LIST]
[*] selecting the usb partition just created
[*]ignore flag on hard disk
[*]do NOT hit the "format" button
[*]hit the "create" button
[/LIST]
Gparted may be installed using the following command:
Gparted then shows up under System-->Administration in the menus.

This fixes my problem. Cheers!

---

### Post by lashi on 2010-05-03
> **shof2k said:**
> Confirmed that GTP-Hanks workaround works. Looks like the program is showing the root device (in my case /dev/sdb), when it wants for a FAT32 partition (/dev/sdb1).


I'll put this on the bug and update my original post.

Thanks Folks


Ok, so, I came across this problem today. The thing is that it is possible to format usb disks without creating a partition map. Ie., it is possible to do mkfs.vfat /dev/sdb -I, where the -I forces it to make the filesystem on the disk. 

I only had /dev/sdb appearing because this was how the VFAT existed on my usb stick. I initially tried to press the eject button, and I realised that this does more than a simple umount.

For those of you who want to get this to work, open a terminal and type in 

sudo umount /dev/sdb

You should replace sdb with whatever the name is of your media device, which you can lookup if you type

df

Anyway, then opening up usb-creator-gtk, you should be able to format and proceed.

- Lashi

---

### Post by virtualXTC on 2012-01-17
None of this has solved the problem for me.

I had a working USB start-up disk for Ubuntu 9.10 (Karmic), but now that we are at 11.10, it seemed a bit much to be doing that many dist-upgrades to get things current on any new systems I wanted to install.

I downloaded a new 11.10 iso, but I am unable to get "Start-Up Disk Creator"  ( usb-creator-gtk )  to accept it.  I can can click on the "Other..." button, and navagate, find and even choose the iso, but after the choce, the file / location isn't saved in the program, and the "Make Startup Disk" button remains greyed out even after I've selected a valid partition.

I tried reformatting the usb drive to see if the program was just not echoing the selection, and it was the drive issue everyone else seemed to be having, but to no avail.  I reinstalled the usb-creator-gtk package as well as the bootable cd package, but that also didn't help.

Update:
I ran again from the terminal and got the error:
isoinfo: Short read on old image

I looked it up and it means the iso was bad.  Re-downloading the iso solved the problem.

---

