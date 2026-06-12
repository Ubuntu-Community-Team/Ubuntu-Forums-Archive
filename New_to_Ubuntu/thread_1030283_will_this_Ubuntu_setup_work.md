---
title: "will this Ubuntu setup work"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-01-04
Going to wean myself from Windozs.
Here is my setup: Running Windows Vista, two HDs, System Commander by Avanquest.
Windows Vista is on the 1st HD. Want to put Ubuntu on the 2nd HD.
System Commander is a boot and partitioning program. This should let me point to the 2nd hd. So I download Ubuntu to a CD. The HD has been formatted. Call up System Commander and point to the 2nd HD. Load the Ubuntu CD and try to install Ubuntu. Question is will this install Ubuntu? Personally I don't think Ubuntu will start up and install this way.
Thanks for any suggestions.

---

### Post by oilchangeguy on 2009-01-04
> **Jack Shankle said:**
> Going to wean myself from Windozs.
Here is my setup: Running Windows Vista, two HDs, System Commander by Avanquest.
Windows Vista is on the 1st HD. Want to put Ubuntu on the 2nd HD.
System Commander is a boot and partitioning program. This should let me point to the 2nd hd. So I download Ubuntu to a CD. The HD has been formatted. Call up System Commander and point to the 2nd HD. Load the Ubuntu CD and try to install Ubuntu. Question is will this install Ubuntu? Personally I don't think Ubuntu will start up and install this way.
Thanks for any suggestions.

this may help:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

and you don't need this system commander. uninstall it if you can.

---

### Post by Jack Shankle on 2009-01-04
Thanks for replying oilchangeguy.
The link you gave will add Ubuntu to the same HD.
I have Windozs Vista on HD 1.
Want to put Ubuntu on HD 2.
So how do I do that?
I think I would need a program like System Commander to switch
to the 2nd HD because the system will boot to HD1 and I must switch it to
HD 2.

---

### Post by oilchangeguy on 2009-01-04
> **Jack Shankle said:**
> Thanks for replying oilchangeguy.
The link you gave will add Ubuntu to the same HD.
I have Windozs Vista on HD 1.
Want to put Ubuntu on HD 2.
So how do I do that?
I think I would need a program like System Commander to switch
to the 2nd HD because the system will boot to HD1 and I must switch it to
HD 2.

i see you have not done much research on dual booting. ubuntu's boot record (grub) will overwrite windows boot record. so you don't need software to help you point to whatever hard drive. done properly you'll get a list (grub) that will allow you to pick the os you want to boot.

---

### Post by oldos2er on 2009-01-04
> **Jack Shankle said:**
> Thanks for replying oilchangeguy.
The link you gave will add Ubuntu to the same HD.
I have Windozs Vista on HD 1.
Want to put Ubuntu on HD 2.
So how do I do that?
I think I would need a program like System Commander to switch
to the 2nd HD because the system will boot to HD1 and I must switch it to
HD 2.

 You don't need any other software than an Ubuntu LiveCD. Use manual installation to point the installer to your second hard disk. Grub will automatically be installed to the MBR of your first disk.

---

### Post by handydan918 on 2009-01-04
> **Jack Shankle said:**
> Thanks for replying oilchangeguy.
The link you gave will add Ubuntu to the same HD.
I have Windozs Vista on HD 1.
Want to put Ubuntu on HD 2.
So how do I do that?
I think I would need a program like System Commander to switch
to the 2nd HD because the system will boot to HD1 and I must switch it to
HD 2.

Do you really think everyone who dualboots has to use some kind of commercial software to do it? Ubuntu uses GRUB, which is capable of booting hundreds of O/S's on the same system. Just follow the tutorial, and post back if you bump your head.

---

### Post by cmcrgl on 2009-01-06
You might find this link useful in setting up Ubuntu to work with System Commander.  

[http://ubuntuforums.org/showthread.php?p=4147910#post4147910](http://ubuntuforums.org/showthread.php?p=4147910#post4147910)

I have yet to try it myself, but is seems to a straightforward procedure.  I will post back here to report on my success or failure.

I have System Commander V9, and while it may not be necessary to use a 3rd party app like System Commander to set up a multiple boot, some of us who have been using such software for years would like to be able to keep on using it.  Personally, I have been using versions of System Commander for more than a dozen years.

---

### Post by Jack Shankle on 2009-01-06
You see there are differences of option about System Commander.
What is one new to Ubuntu to do?
At this time I guess I would go with uninstalling System Commander and see how Ubuntu will handle the problem.
HD 1 is partitioned with two Vista Partitions and no free space.

Hd 2 has been formatted with FAT 32 and is all free space.

I have downloaded Ubuntu to the computer and made a DVD of the
download. I will next uninstall System Commander.
I have a good backup of my present system.
I panic about going any further.

---

### Post by DGortze380 on 2009-01-06
Just boot the cd you made. Follow the steps, it walks you through. When you get to partitioning, select your SECOND disk. This won't be denoted as D:\ ... that's a windows thing. Your second disk will be something like hdb0 or sdb0. Partition the whole disk as ext3, then create another partition on the disk (1.5x your RAM) format it as swap. Continue with your install.

---

### Post by sadaruwan12 on 2009-01-06
Hi,

You really need to research on dual booting. With Ubuntu or any other distribution of Linux there is a free boot manager program that ge auto configured when you finish the installation only what you have to do partition the hard disk the way you want.

Here follow this guide [*[COLOR="RoyalBlue"]The Perfect Desktop[/COLOR]*]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron").

Your hard disks will want look like C:, D: like partitions like in the windows they differ if you've a PATA or an IDE hard disk it'll be listed like this "hda" or "hd0" if you have another hard disk it'll be "hdb" or "hd1" ('cos numbering starts from 0) this goes on and if you've a SATA hard disk it'll be listed like this "sda" or "sd0" for the first hard disk for the second hard disk will be "sdb" or "sd1". When partition the hard drive the partition table will start from 0 and your first partition will look like "sd0,0" that means first hard disk first partition so the second partition looks like "sd0,1" that means first hard disk second partition. If you're on the second hard drive then it'll be listed like this "sd1.0" that means second hard disk first partition I think you get the idea right about now. So try this and you want going to need any commercial software for that.

---

### Post by Jack Shankle on 2009-01-06
Thanks Guys for all your help. It must be aggravating answering all these
questions over and over again. My hats off to you.

I now have Ubuntu on the 2nd HD. On the 1st HD still resides the 2 partitions with Windows Vista.

However I know longer have a Windows Vista desktop. I read somewhere that I have to export the bookmarks from Thunderbird before I can import them to Ubuntu.
Same with FireFox. I don't know where there is a tut for exporting bookmarks. I guess I would have to do that before importing them into Ubuntu. Again I have NO Windows desktop anymore to do this.

The install was not an easy thing. Some of the windows offered no help
and I had to guess what the proper response should be. Ex: I had to guess
and put a "/" not knowing what it was for.

---

### Post by DGortze380 on 2009-01-06
> **Jack Shankle said:**
> Thanks Guys for all your help. It must be aggravating answering all these
questions over and over again. My hats off to you.

I now have Ubuntu on the 2nd HD. On the 1st HD still resides the 2 partitions with Windows Vista.

However I know longer have a Windows Vista desktop. I read somewhere that I have to export the bookmarks from Thunderbird before I can import them to Ubuntu.
Same with FireFox. I don't know where there is a tut for exporting bookmarks. I guess I would have to do that before importing them into Ubuntu. Again I have NO Windows desktop anymore to do this.

The install was not an easy thing. Some of the windows offered no help
and I had to guess what the proper response should be. Ex: I had to guess
and put a "/" not knowing what it was for.

/ is the root of the file system, similar to C:\ in windows

When you start your computer, it should say to press ESC for a menu (or just so the menu by defualt). Choose Vista (Longhorn) for Vista, Ubuntu for Ubuntu. You can only have one at a time. They are two totally different operating systems. You won't have access to the Vista Desktop or applications from Ubuntu and vice versa. You should eb able to access your vista files in Ubuntu though.

---

### Post by Jack Shankle on 2009-01-06
I found the 2 Vista Longhorn entries and tried both of them. They go out to a blank screen and come back to the same Dual Boot screen.
The one for Ubuntu will take me to Ubuntu.  
In other words I can't get into either of the Vista Partitions.

---

### Post by DGortze380 on 2009-01-06
> **Jack Shankle said:**
> I found the 2 Vista Longhorn entries and tried both of them. They go out to a blank screen and come back to the same Dual Boot screen.
The one for Ubuntu will take me to Ubuntu.  
In other words I can't get into either of the Vista Partitions.

One of those Vista Partitions is a Recovery Partition. The other is your install. You may have to google fixmbr

---

### Post by Jack Shankle on 2009-01-06
Taking a step back and rethinking Ubuntu.
I restorred both my Windows Vista partitions on HD 1.
Then using System Commander formatted the 2nd HD that Ubuntu was on. I'm not giving up but I had to get to my email in Thunderbird and my web addresses in Firefox. Couldn't get the hang of this in Ubuntu. Also the selection screen in Ubuntu wouldn't allow me to select either Vista partition. Yes I could get to my Vista files in Ubuntu but not Thunderbird or Firefox files. Either the type of Dual Booting I am doing Ubuntu will not handle OR I am to stupid
to figure it out. Will try to do a lot of reading and not bug you guys anymore.

---

