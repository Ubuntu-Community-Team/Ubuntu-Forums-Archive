---
title: "Boot error!"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by Amory_Blaine on 2009-11-20
Installed Ubuntu 9.10 last night.  Installation didn't give me any problems.

After the installation I try to reboot and get an error saying this:

GRUB Loading
error: no such disk
grub rescue>

I have 3 hard drives in my computer.  On one of the sata drives is Windows 7 and on one of the others in Ubuntu.  I would like to get the option to boot from Windows or Ubuntu.

I found a couple things online where I need to set something that says ms-sys, but that gave me an error (can't find the page right now, sorry).

New to Ubuntu, very familiar with OS X and all versions of Windows.

Thanks in advance!

---

### Post by lotharmat on 2009-11-20
Dumb question time...

Is your HDD recognised in your BIOS?

---

### Post by Amory_Blaine on 2009-11-20
yes, all the HDDs are showing up in the bios.

There was no problem before installing Ubuntu.  I loaded up from the disk and it still shows all the files there just fine on all HDDs.  

Must be MBR problem, but have no idea where to even start with that.

---

### Post by philinux on 2009-11-20
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

This might help. Did you let the installer do the default grub install? Or did you click advanced and specify a partition/location?

---

### Post by Amory_Blaine on 2009-11-20
The first time I let it just do the install itself.  

The next time I tried to install it off of the Windows 7 drive (just testing it).  Still no, luck.

Thanks for the link.  I will take a look at it.

---

### Post by kansasnoob on 2009-11-20
> **Amory_Blaine said:**
> The first time I let it just do the install itself.  

The next time I tried to install it off of the Windows 7 drive (just testing it).  Still no, luck.

Thanks for the link.  I will take a look at it.

I don't understand this:

> The next time I tried to install it off of the Windows 7 drive (just testing it).

But it would answer a lot of questions if you'd boot the Live CD choosing to Try without changes........ and then run the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

The results of that will answer many questions.

---

### Post by Amory_Blaine on 2009-11-20
The question was: 

Did you let the installer do the default grub install? Or did you click advanced and specify a partition/location?

The first time I let it do default and the second time I selected the partition that has windows 7 on it.

I will look into what you said kansasnoob.  Thanks for the help so far everyone.

---

### Post by Amory_Blaine on 2009-11-21
Thanks for all the help.  Here is what ended up being the problem...

I have 3 hard drives.  My main is a 500GB Sata drive and have 2 IDE drives.

I installed Ubuntu on an IDE drive and when I booted from the disk, it would not show the drive.

I have had a lot of problems with this computer and being able to use an IDE drive as my main drive.  Windows will not allow it either.

I made a partition on my SATA drive, installed Ubuntu on it and it worked just fine!  I had to reformat my windows 7 drive, which was fine because I had just reinstalled it and got all the files off of it that I wanted when I was booted from the Ubuntu disk.

Thanks again for help!  I am enjoying it very very much!

---

