---
title: "External HDD format questions"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by clockworktri on 2009-12-30
I just bought an external usb WD (Elements, 1tb) hard drive for my laptop. I removed the System Volume Information file because all it held was the automatic backup program for Windows (which I no longer run at all). At least, I'm pretty sure that's all it held. Anyway, now it does not register as a hard drive when I mount it. I mean, it mounts, but the icon that shows up is the generic file icon. 

I am wondering if 
a) there is a simple thing I can do that will make my lappy register it as a HD and give it the correct icon all on its own. 
and
b) if I should format it. I poked around the formatting posts and realized that I don't really know what this entails. Is it already formatted? Did removing the files that came with it make it incompatible with the Mac/Windows OS's? While I won't be switching operating systems, I may want to hook this up to my sister's mac or a friend's windows. But I also don't want to use up much room with a partition or anything. So... do I even need to do anything to it? Should I leave it as-is or is formatting it necessary or will it make it better/easier to use or something? 

I realize that's a lot of rambling questions, but I can't seem to find this info on my own, so I'd really REALLY appreciate it if someone could let me know? Thanks!

---

### Post by benfindlay on 2009-12-30
Deleting files on the drive should not make any difference to accessibility or cross platform compatibility. What will make a difference is the file-system the drive is formatted with. If you are wanting to potentially use it with Windows, Mac and Linux machines, I would recommend the FAT32 file-system, however it has an individual file size limit of approximately 4GB, meaning you may run into problems if you want to store hi-def video.

Regarding access to your drive, you may have done something else to it to cause your mounting problems. I would recommend installing gparted from synaptic and reformatting the drive using gparted's GUI.

---

### Post by Bartender on 2009-12-30
clockwork -
I would suggest downloading the latest stable version of GPartedLiveCD.  Link under my sig.  The download you probably want is the plain old 386-iso.  That's the one that's compatible with most any PC.  You burn the download to a CD like you would any Linux install CD.  In other words, don't just copy the data, it must be converted to a bootable CD.  This can be done on a Windows PC just as readily as a Linux PC.

What you have when you get done is a bootable CD that's a great stand-alone partitioning tool or just an informational tool.  Boot from the optical drive, then when you get to the partition map look in the upper right corner for the little box that lets you choose drives.  If the disk can be read at all, Gparted will tell you how many partitions exist, and how they're formatted.  I imagine the external disc is formatted as ntfs, but GParted will tell you for sure.  And if you think you screwed something up by removing those files, you can use Gparted to delete all partitions on the disk, then set it up however you want.  

I don't even know what file systems a Mac uses :confused: oh, wait, wikipedia says HFS +.  I don't think GParted does HFS+, but it does do FAT32.  Which isn't a very efficient file system, but you could always format most of the drive as NTFS and part of it FAT32.  You could format part of it as ext4, part as NTFS, and part as FAT32 if you wanted.

This is assuming you don't want to install Linux, you just want to use this as a back-up and data storage device that's useful no matter whose system you plug it into...

---

### Post by Sef on 2009-12-30
> I don't even know what file systems a Mac uses :confused: oh, wait, wikipedia says HFS +.  I don't think GParted does HFS+

Incorrect.  [GParted does do HFS+]("http://gparted.sourceforge.net/features.php").   It cannot grow or label it though.

---

### Post by halitech on 2009-12-30
Since the OP is dealing with an external drive, why bother worrying about getting the stand alone Gparted Live cd? why not just use Gparted from the install? Also eliminates doing something stupid like formating the wrong drive and wiping the installed system since it will be mounted.

---

### Post by audiomick on 2009-12-30
> **halitech said:**
> Since the OP is dealing with an external drive, why bother worrying about getting the stand alone Gparted Live cd? why not just use Gparted from the install? Also eliminates doing something stupid like formating the wrong drive and wiping the installed system since it will be mounted.

Sounds like a good idea to me.

---

