---
title: "Need help setting up a dual boot (XP, ubuntu)"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by nash black on 2010-04-21
Hi

I am currently running windows xp pro (sp3) on my computer, but I have a new hard drive and I would like to use some of that new space to install a second, Linux based operating system and I want to know if it is possible to do the following:

-Keep XP on my original, 160GB drive

-Install Ubuntu on one partition of the new, 400GB drive, leaving part of it accessible to both operating systems

-Give Linux access to my windows file system without giving windows access to the Linux partition

And finally, if this would be possible, how would I select an operating system at start-up, would I have to select the boot device at start-up normally (F11 for me, etc) or is there a more streamlined way? It would be nice if I could set it up to automatically boot one operating system if I don't select the other one in a set period of time (say 10-30 seconds) 

I currently have the new hard drive installed and formatted, running with the original hard drive but nothing is on it, so overwriting the new drive is not an issue. I am currently downloading an image of Ubuntu 9.10, but I really have no idea what to do from there, so I'll need some help! Info about whether or not the things I mentioned above will be possible and how to do them would be a great start.

Thanks,
Nash

---

### Post by MeNtuxRoKinU on 2010-04-21
You can keep XP for sure. 

Create a new partition on the new HD to whatever size you want to run Linux.

Install from your image disc, choosing the partition you created. Then reboot.

Grub will ask you which machine you want to start from. 

It's [COLOR=Red]almost[/COLOR] that easy! Sorry, can't help out with all the cross platform access questions.

---

### Post by ed-koala on 2010-04-21
What you want to do is exactly what Ubuntu does by default.  Linux can read files from Windows, Windows cannot read files from Linux.

As the above poster said .. set up a partition to install Ubuntu on and it will do the rest, including set up a boot screen where you choose which OS you want to boot to, and it will automatically boot to the default OS in 10 seconds.

---

### Post by Zintha on 2010-04-21
Yeah, you're asking for what already happens!

Just put in a Live CD and partition the hard drive then install your chosen OS onto it!
All of the stuff you want happens as standard!

---

### Post by nash black on 2010-04-21
Ha well I guess that's perfect. I'll try it out soon.

thanks

---

### Post by ssulaco on 2010-04-21
> **nash black said:**
> Hi

I want to know if it is possible to do the following:
-Keep XP on my original, 160GB drive
-Install Ubuntu on one partition of the new, 400GB drive, leaving part of it accessible to both operating systems

The way I did it was plug the XP drive in as "slave" and the new drive as "master"....during the partioning stage of the install make note of how the Ubuntu (master) drive is designated.
(/dev/sda, /dev/sdb, etc),then near the end of the installation process there is an "Advanced" button in the lower right that you can click on & type in where to install grub, e.g. if your Ubuntu drive is sda, type in /dev/sda in place of the default (hd0). This should ensure that grub is installed to the mbr of the Ubuntu drive.....also you might check your bios to ensure the primary slave drive is either on or set to auto...
you might be interested in reading this also
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
> **nash black said:**
> And finally, if this would be possible, how would I select an operating system at start-up, would I have to select the boot device at start-up normally (F11 for me, etc) or is there a more streamlined way? It would be nice if I could set it up to automatically boot one operating system if I don't select the other one in a set period of time (say 10-30 seconds)
Grub is Ubuntu's boot loader....with the option of booting into Windows or Ubuntu
[http://news.softpedia.com/images/extra/LINUX/large/grub2karmic-large_001.jpg](http://news.softpedia.com/images/extra/LINUX/large/grub2karmic-large_001.jpg)

---

### Post by oldfred on 2010-04-22
You want to be sure to install grub to sdb (the new drive) not your windows drive. There is an advanced button just at the end of the  partitioning of the drive before (or as) you click install. Choose sdb to install grub to and then in BIOS select the new drive to boot as default.

Install karmic Screens shown and advanced screen shown:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by egalvan on 2010-04-22
> **nash black said:**
> 

-Install Ubuntu on one partition of the new, 400GB drive,
** leaving part of it accessible to both operating systems**

At this point in time, NTFS is the best choice for a partition that will be accessed by Windows & Linux.

> -Give Linux access to my windows file system without giving windows access to the Linux partition

Windows doesn't know diddly about Linux *anything*, much less partitions, so you are OK on this.

>  I am currently downloading an image of Ubuntu 9.10,

The latest Ubuntu, Lucid Lynx 10.04 LTS, is almost here.
Eight days.
It's due on the 29th of April...

You may want to consider waiting until then....
Lucid will be a Long Term Support version, which means it has been tested more so than the normal releases.

Run Karmic 9.10 as a LiveCD until then... it will be a learning experience
Or go for a full install, and really learn something.

> [B]I really have no idea what to do from there, so I'll need some help!
[/B] Info about whether or not the things I mentioned above will be possible and how to do them would be a great start.


all of us here had to learn Linux on the way to the Forum :)
None of us were born knowing everything...
So you will fit right in.

Welcome

---

### Post by nash black on 2010-04-22
Thanks everyone

I've got it installed as I wanted... Much faster and easier than I expected!

---

