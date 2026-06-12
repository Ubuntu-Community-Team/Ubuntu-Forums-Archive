---
title: "Restore MBR?"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by rgroene on 2009-08-15
I recently got a new laptop, and I set it up for dual boot with Windows Vista and Ubuntu (with a third FAT32 partition for files). It was working fine for a few days, and then the hard drive stopped working. For a while, it would say "internal hard drive not found," but then it started to bring up Grub, only to have it quickly terminate with "error 17" or "error 5." I'm not sure what the problem is, but this happened after running Norton 360 on Windows Vista. Before I tried to install it, I booted into Windows. It took a long time to bring up the screen with boot options, but it worked. Then, when I tried to install Norton 360 from the CD, it froze up. When I rebooted my computer, it brought up some recovery utility (I couldn't tell whether it was associated with Vista or Norton 360, but then it gave me an error message). When I tried to reboot, after that, nothing worked. Thus, I'm thinking this might be a problem with the master boot record. Is there a way that grub can be reinstalled and that the MBR can be restored so that I do not have to completely reformat my hard drive? Note that I tried booting from a Live CD, but it would not recognize any of my partitions at all. When I went to install, it DID recognize my hard drive.

---

### Post by Wiebelhaus on 2009-08-15
Seriously , this is all a coincidence. It sounds like your banging your head with a failing hard drive and considering how [cheap the are now]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=380&name=Laptop-Hard-Drives") , replace it.

P.S Get Western Digital!

---

### Post by alexlafreniere on 2009-08-15
So when you booted into your LiveCD, you couldn't read data off any of the partitions but could boot into Vista?

---

### Post by rgroene on 2009-08-15
I've already called Dell Support, and they're sending me a replacement (it's still covered under warranty--I've only had the computer for a few days). Because the computer is so new, it seemed odd that the hard drive would already be fried. I'm getting another one anyway, but I really don't want to reinstall everything. I spent a long time getting all the stuff I needed installed, customizing the look and feel of the operating systems, etc., and I don't want to redo all of that.

I cannot boot off of the hard drive at all (into Vista or Ubuntu), and I can't access the files from it when I boot up with a Live CD. What I was saying is that the installer does recognize it when I boot up with a Live CD.

I thought the Norton thing probably was just a coincidence, but I was just trying to make sure because everything was working perfectly until the moment I put that CD in.

---

### Post by Megaptera on 2009-08-15
You could try 'slaving' the old hard drive when the new machine arrives. I did a quick google and found this:
[http://www.dtidata.com/resourcecenter/2007/04/23/how-to-slave-hard-drive/](http://www.dtidata.com/resourcecenter/2007/04/23/how-to-slave-hard-drive/)

While you're waiting for your new machine you could research this opition for your particular makes/models/specs possibly?

---

### Post by rgroene on 2009-08-15
I'm sorry; my last post was unclear.

What I was saying is that they are sending me a new hard drive, not a new computer.

---

### Post by LewRockwell on 2009-08-15
I seriously doubt that your hard drive is bad

I'd try the Super Grub Disk
(it has manual and automatic functioning and so experiment with it)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by louieb on 2009-08-15
> **rgroene said:**
>  Thus, I'm thinking this might be a problem with the master boot record. Is there a way that grub can be reinstalled and that the MBR can be restored so that I do not have to completely reformat my hard drive? 

This doesn't sound like an MBR problem - it does sound like a hard drive going bad. Its been my experience that hard drives die in the 1st few months or they last for years.   But since you asked.  as **LewRockwell** says theres Super Grub. 
Or heres a tried and true method putting Grub back in the MBR. [Fix Grub after Win install - catlett]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")  this would work in your case too. 

Depending on the health of the old drive you may be able to clone it to the new. You'll just need a USB enclosure and [Clonezilla]("http://www.clonezilla.org/") 

One last note [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")  has program GSmartMon 
> GSmartControl is a graphical user interface for smartctl (from Smartmontools package), which is a tool for
querying and controlling SMART (Self-Monitoring, Analysis, and Reporting
Technology) data on modern hard disk drives. It allows you to inspect the
drive's SMART data to determine its health, as well as run various tests on
it.
as a bonus it also has Clonezilla and Super Grub.

---

### Post by rgroene on 2009-08-17
Yeah, I think you're right. It seems that the drive is going bad.

I tried the Super Grub thing, but it didn't do any good. The other method also doesn't work.

I even tried to reformat it, which failed--so I'm pretty certain the hard drive is fried.

But, in any case, I have the new one being mailed to me; I only hope it's here in time for college (I go back 2 Saturdays from now). In the mean time, I can still use my hard drive from my older laptop, which is still a pretty new hard drive (250 GB).

But thanks for all the help anyway. The Super Grub disk might come handy in the future.

---

### Post by trilobite on 2009-08-17
> **rgroene said:**
> Yeah, I think you're right. It seems that the drive is going bad.

I tried the Super Grub thing, but it didn't do any good. The other method also doesn't work.

I even tried to reformat it, which failed--so I'm pretty certain the hard drive is fried.

But, in any case, I have the new one being mailed to me; I only hope it's here in time for college (I go back 2 Saturdays from now). In the mean time, I can still use my hard drive from my older laptop, which is still a pretty new hard drive (250 GB).

But thanks for all the help anyway. The Super Grub disk might come handy in the future.

Hi - 
 
I've found "Smart Boot-Manager" to be outstanding. It is really easy to use, and (in my experience) very reliable. I highly recommend it! Here's the URL - 
[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/) 

It's small enough to fit on a floppy (if you still have a floppy drive), but there are also CD images available, I believe. 
- trilobite

---

