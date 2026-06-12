---
title: "Old PC - New Disk - Dual boot - Do I need to format disk?"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by stdojo on 2010-07-10
New problem - Any help will be appreciated
I have Ubuntu installed BUT I installed PLOP before UBUNTU.  When I re-boot I only have the option of selecting PLOP or WIN, not UBUNTU option.  I believe that I need to modify my boot.ini file but I'm not sure exactly what I need to add to boot.ini to give me the UBUNTU option.
Thanks!
Steve

I apologize if this has already been covered someplace.  After many years of using Win, I'm going to make the big plunge.  I want to set up my desk top to dual boot, but I'm going to install a new hard disk and **dedicate it to Ubuntu** before I install the new OS.  Should I format my new disk for Win before I do the Ubuntu install?  Thanks in advance.  Steve

---

### Post by Jerry N on 2010-07-11
> **stdojo said:**
> I apologize if this has already been covered someplace.  After many years of using Win, I'm going to make the big plunge.  I want to set up my desk top to dual boot, but I'm going to install a new hard disk before I install Ubuntu.  Should I format my new disk for Win before I do the Ubuntu install?  Thanks in advance.  Steve

I use Parted Magic (or sometimes Puppy Linux) to format the hard drive just the way I want it before installing anything and I don't let the installation programs do their own partitioning.  You should install Windows in its partition (Probably NTFS) PRIOR to installing Ubuntu.  It is possible to do it the other way around (I haven't) but Windows first is the easiest.  

That's my way, but certainly not the only way.

Jerry

---

### Post by john newbuntu on 2010-07-11
No you do not need to format it to win.  If you have an Ubuntu liveCD or USB, there is a tool in there called gparted.  This is a graphical tool that helps you choose the disk, partition and format it anyway you want it (with certain limitations of course).  Here's a part of its documentation:
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

The other (easier) option is to just give the installer the entire disk and it can do the formatting and partitioning for you automatically.

I hope you are aware that without even installing anything, you could test drive ubuntu straight from the liveCD.

---

### Post by mapes12 on 2010-07-11
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by Paqman on 2010-07-11
> **stdojo said:**
> Should I format my new disk for Win before I do the Ubuntu install?

You definitely want to install Windows first. Depending on what version of Windows you're installing it might just be easier to install to the whole disk with Windows, then partition during the Ubuntu install. Older versions of Windows don't have particularly good partitioning tools in the installer.

---

### Post by john newbuntu on 2010-07-11
The way I understood the question was that you already have windows in one drive and that you need to install ubuntu on the second. 
If what I understood is not right. i.e, if you are just sticking to one drive on your computer with both win and ubuntu, then what paqman said is right. Install windows first and then ubuntu just to make things a bit easier. (although I have done it the other with XP and repaired the MBR later.)

---

### Post by stdojo on 2010-07-11
Thanks Jerry!

---

### Post by stdojo on 2010-07-11
Easy sounds good.  How do I "give" the installer the entire disk without formatting it?

---

### Post by -kg- on 2010-07-12
> **stdojo said:**
> Easy sounds good.  How do I "give" the installer the entire disk without formatting it?

The installer of either Windows or Ubuntu will create and format their own partitions.  It's not required to have any partitions at all...just the free space.

My suggestion would be to create a Windows partition using GParted from the Live CD that covers as much of the hard drive that you want Windows to take.  Then, when installing Windows, you'll need to specify that Windows install into that partition only.  The reason for this is this:

At any time, a Windows partition is difficult and somewhat dangerous to resize.  If you're using XP and before, it's not quite as difficult, but you need to defrag Windows before performing these operations.  Don't think that you're OK because you just installed it, either.  Some of the worst fragmentation I've ever come across was just after a fresh installation.  It will be ***massively fragmented!*** (Thanks, Micro$oft! :roll: )

Vista and beyond have their own way of setting things up, and defragmenting won't change some of these things.  There are certain system files that will be put on a certain place on the partition, and they can't be moved.  With the partitions on which these OSes are installed, the only way to (relatively) safely shrink the partitions is with their own Partition Manager tool.  Even then, you'll be surprised at the amount of free space left when the limit of how much you can shrink the partition is reached.

The only way to get around this is to create the partition beforehand, at the size that you want them to be.  No resizing of the partition is necessary and you avoid all the hassle.  Then install Ubuntu in the remaining free space on your drive.

Yes, I would recommend you install Windows first and Ubuntu second.  Windows likes to be the first partition on the hard drive, and I've heard it is required by BIOS on some computers.  It's not really a problem, in any case, and it saves you the hassle of having to reinstall GRUB when Windows takes over the MBR when ***it*** is installed second.

When you install Ubuntu (2nd), it replaces the Windows boot loader with GRUB, which will detect your Windows installation and include it in its menu as a boot option.  You're in like flint! :)

For more information on partitions and partitioning operations, read at the link in my signature block.

---

### Post by audiomick on 2010-07-12
> **stdojo said:**
> Easy sounds good. [COLOR=Red] How do I "give" the installer the entire disk [/COLOR]without formatting it?

If the disc is empty, you can just tell the installer to use the unallocated space. If you want to (at least feel like you have it) under precise control, choose the manual option when the installer comes to the partitioning bit, create the partitions you want yourself and tell it to install from there. 

Don't worry too much, it is all pretty self-explanatory when you see it.
Don't forget: the installer doesn't do anything without asking for confirmation. If you get worried, you can bail out and come and ask more questions.

---

### Post by stdojo on 2010-07-13
Thanks for all the help and advice.  Just to clarify, I plan to dedicate the new disk to Ubuntu.

---

### Post by stdojo on 2010-07-22
I finally got my USB wireless dongle on my desktop working with Ubuntu.  I spent an embarrassing amount of time on this.  I see this as a major impediment for many potential Ubuntu users.  A simplified tool for addressing this really needs to be developed.  I would help with this but to be perfectly honest I tried so many things and read so much on this topic I'm not sure what finally got it working.  If anyone thinks it would be helpful I could try & recreate my steps.  Thank you to those that replied to my earlier posts and I'm sure that I'll be back with more as I learn more about this OS.

---

